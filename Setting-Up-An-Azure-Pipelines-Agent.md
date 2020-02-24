Manually done changes to the current builders that need be integrated into the below next time we replace agents:
* Install Python 3.8.1.

Steps taken to set up a build machine. These are how @BillyONeal set up our agents:

* Get an Azure VM created. The current build agents are `B8ms` sized machines.
* Log in and create a powershell script with the following content:

```
# Copyright (c) Microsoft Corporation.
# SPDX-License-Identifier: Apache-2.0 WITH LLVM-exception

# Sets up VM for use as a build machine

$AzureDevOpsURL = 'https://dev.azure.com/vclibs/'
$AzureDevOpsPool = 'STL'
$PersonalAccessToken = 'CHANGE THIS'

$WorkLoads =  '--add Microsoft.VisualStudio.Component.VC.CLI.Support ' + `
              '--add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 ' + `
              '--add Microsoft.VisualStudio.Component.VC.Tools.ARM64 ' + `
              '--add Microsoft.VisualStudio.Component.VC.Tools.ARM ' + `
              '--add Microsoft.VisualStudio.Component.Windows10SDK.18362 '

$ReleaseInPath = 'Preview'
$Sku = 'Enterprise'
$VSBootstrapperURL = 'https://aka.ms/vs/16/pre/vs_buildtools.exe'
$CMakeURL = 'https://github.com/Kitware/CMake/releases/download/v3.16.1/cmake-3.16.1-win64-x64.msi'
$LlvmURL = 'https://releases.llvm.org/9.0.0/LLVM-9.0.0-win64.exe'
$NinjaURL = 'https://github.com/ninja-build/ninja/releases/download/v1.9.0/ninja-win.zip'
$VstsAgentURL = 'https://vstsagentpackage.azureedge.net/agent/2.160.1/vsts-agent-win-x64-2.160.1.zip'

$ErrorActionPreference = "Stop"

Function InstallVS
{
  Param(
    [String]$WorkLoads,
    [String]$Sku,
    [String]$VSBootstrapperURL)
  $exitCode = -1
  try
  {
    Write-Host "Downloading VS bootstrapper ..."
    [string]$bootstrapperExe = Join-Path ${env:Temp} ([System.IO.Path]::GetRandomFileName() + ".exe")
    Invoke-WebRequest -Uri $VSBootstrapperURL -OutFile $bootstrapperExe

    $Arguments = ('/c', $bootstrapperExe, $WorkLoads, '--quiet', '--norestart', '--wait', '--nocache')

    Write-Host "Starting Install: $Arguments"
    $process = Start-Process -FilePath cmd.exe -ArgumentList $Arguments -Wait -PassThru
    $exitCode = $process.ExitCode

    if ($exitCode -eq 0 -or $exitCode -eq 3010)
    {
        Write-Host -Object 'Installation successful!'
    }
    else
    {
        Write-Host -Object "Nonzero exit code returned by the installation process : $exitCode."
        exit $exitCode
    }
  }
  catch
  {
    Write-Host -Object "Failed to install Visual Studio!"
    Write-Host -Object $_.Exception.Message
    exit $exitCode
  }
}

Function InstallMSI
{
    Param(
        [String]$Name,
        [String]$Uri
    )

    try
    {
        Write-Host "Downloading $Name..."
        [string]$randomRoot = Join-Path ${env:Temp} ([System.IO.Path]::GetRandomFileName())
        [string]$msiPath = $randomRoot + '.msi'
        [string]$msiExecPath = 'msiexec.exe'
        $args = @('/i', $msiPath, '/norestart', '/quiet', '/qn')

        Invoke-WebRequest -Uri $Uri -OutFile $msiPath
        Write-Host "Installing $Name..."
        $process = Start-Process -FilePath $msiExecPath -ArgumentList $args -Wait -PassThru
        $exitCode = $process.ExitCode

        if ($exitCode -eq 0 -or $exitCode -eq 3010)
        {
            Write-Host -Object 'Installation successful!'
        }
        else
        {
            Write-Host -Object "Nonzero exit code returned by the installation process : $exitCode."
            exit $exitCode
        }
    }
    catch
    {
        Write-Host -Object "Failed to install $Name!"
        Write-Host -Object $_.Exception.Message
        exit -1
    }
}

Function InstallZip
{
    Param(
        [String]$Name,
        [String]$Uri,
        [String]$Dir
    )

    try
    {
        Write-Host "Downloading $Name..."
        [string]$randomRoot = Join-Path ${env:Temp} ([System.IO.Path]::GetRandomFileName())
        [string]$zipPath = $randomRoot + '.zip'
        Invoke-WebRequest -Uri $Uri -OutFile $zipPath
        Write-Host "Installing $Name..."
        Expand-Archive -Path $zipPath -DestinationPath $Dir
    }
    catch
    {
        Write-Host -Object "Failed to install $Name!"
        Write-Host -Object $_.Exception.Message
        exit -1
    }
}

Function InstallLLVM
{
    Param(
        [String]$Uri
    )

    Write-Host "Downloading LLVM..."
    [string]$randomRoot = Join-Path ${env:Temp} ([System.IO.Path]::GetRandomFileName())
    [string]$installerPath = $randomRoot + '.exe'

    Invoke-WebRequest -Uri $Uri -OutFile $installerPath
    Write-Host "Installing LLVM..."
    Write-Host "Please press next over and over and change no other options."
    $process = Start-Process -FilePath $installerPath -Wait -PassThru
    $exitCode = $process.ExitCode

    if ($exitCode -eq 0 -or $exitCode -eq 3010)
    {
        Write-Host -Object 'Installation successful!'
    }
    else
    {
        Write-Host -Object "Nonzero exit code returned by the installation process : $exitCode."
        exit $exitCode
    }
}

InstallVS -WorkLoads $WorkLoads -Sku $Sku -VSBootstrapperURL $VSBootstrapperURL
InstallMSI 'CMake' $CMakeURL
InstallZip 'Ninja' $NinjaURL 'C:\Program Files\CMake\bin'
InstallLLVM $LlvmURL
InstallZip 'Azure DevOps Agent' $VstsAgentURL 'C:\agent'
Add-MpPreference -ExclusionPath C:\agent
& 'C:\agent\config.cmd' --unattended --url $AzureDevOpsURL --auth pat --token $PersonalAccessToken --pool $AzureDevOpsPool --runAsService

Write-Host "Updating PATH ..."
$environmentKey = Get-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" -Name Path
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" -Name Path -Value "$($environmentKey.Path);C:\Program Files\CMake\bin;C:\Program Files\LLVM\bin"

shutdown /r /t 01
```

* Edit the personal access token in the above script, and then run it from an administrative powershell terminal.
* Sometime during running the script, you'll have to press next a bunch of times for the LLVM installer because it appears to not support unattended install at this time.
* The script will reboot the VM. Upon reboot, log back into the VM and delete the powershell script (so that the PAT doesn't remain on the machine).