Steps taken to set up a build machine. These are how @BillyONeal set up bion-tr-gh-1:

* Install Windows Server 2019, updates, and drivers. (Or use a VM from Azure)
* If not using a VM from Azure, set the machine name to something reasonable.
* Install the "C++ Desktop" workload for Visual Studio 2019 Version 16.4 Preview 2 (or later) from https://visualstudio.microsoft.com/vs/preview/
    * Desktop Workload
        * MSVC v142 tools
        * Windows SDK 10.0.18362
        * C++/CLI Support for v142 Build Tools
    * (go to Individual Components)
        * ARM and ARM64 build tools for the same compiler version.
    * It is recommended that you don't install anything else; in particular you MUST NOT install the Just In Time Debugger as it can cause tests to hang. (When they fail they try to start the Just In Time Debugger, which is great when you're at the machine in person but these machines run unattended.)
* Install CMake 3.15.4 from https://cmake.org/download/, choose the "Add to PATH for all users" option in the installer.
* Download Ninja from https://ninja-build.org/ and copy ninja.exe to CMake's bin directory C:\Program Files\CMake\bin. (This will put it on the PATH under the same entry CMake's installer created)
* Install LLVM 9.0.0 from https://releases.llvm.org/download.html, choose the "Add to PATH for all users" option in the installer. (Note: we test with 9.0.0 because that's what is going to be bundled with Visual Studio soon as of 2019-10-24)
* Follow the instructions at https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops to install the agent. On bion-tr-gh-1 the agent is installed to `C:\agent`. Install the agent as a service that runs as NETWORK SERVICE.

```
PS C:\> .\config.cmd

>> Connect:

Enter server URL > https://dev.azure.com/vclibs/
Enter authentication type (press enter for PAT) >
Enter personal access token > ****************************************************
Connecting to server ...

>> Register Agent:

Enter agent pool (press enter for default) > STL
Enter agent name (press enter for BION-TR-GH-1) >
Scanning for tool capabilities.
Connecting to the server.
Successfully added the agent
Testing agent connection.
Enter work folder (press enter for _work) >
2019-10-24 23:21:31Z: Settings Saved.
Enter run agent as service? (Y/N) (press enter for N) > y
Enter User account to use for the service (press enter for NT AUTHORITY\NETWORK SERVICE) >
Granting file permissions to 'NT AUTHORITY\NETWORK SERVICE'.
Service vstsagent.vclibs.STL.BION-TR-GH-1 successfully installed
Service vstsagent.vclibs.STL.BION-TR-GH-1 successfully set recovery option
Service vstsagent.vclibs.STL.BION-TR-GH-1 successfully set to delayed auto start
Service vstsagent.vclibs.STL.BION-TR-GH-1 successfully configured
Service vstsagent.vclibs.STL.BION-TR-GH-1 started successfully
PS C:\>
```