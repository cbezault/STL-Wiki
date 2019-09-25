Steps taken to set up a build machine. These are how @BillyONeal set up bion-x299-gh:

* Install Windows Server 2019, updates, and drivers. (Or use a VM from Azure)
* If not using a VM from Azure, set the machine name to something reasonable.
* Install the "C++ Desktop" workload for Visual Studio 2019 Version 16.4 Preview 1 from https://visualstudio.microsoft.com/vs/preview/
    * Desktop Workload
        * MSVC v142 tools
        * Windows SDK 10.0.18362
        * C++/CLI Support for v142 Build Tools
    * (go to Individual Components)
        * ARM and ARM64 build tools for the same compiler version.
    * It is recommended that you don't install anything else; in particular you MUST NOT install the Just In Time Debugger as it can cause tests to hang.
* Install CMake 3.15.3 from https://cmake.org/download/, choose the "Add to PATH for all users" option in the installer.
* Download Ninja from https://ninja-build.org/ and copy ninja.exe to CMake's bin directory C:\Program Files\CMake\bin. (This will put it on the PATH under the same entry CMake's installer created)
* Install LLVM 8.0.1 from http://releases.llvm.org/download.html, choose the "Add to PATH for all users" option in the installer. (Note: we test with 8.0.1 because that's what is currently bundled with Visual Studio as of 2019-09-24)
* Follow the instructions at https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-windows?view=azure-devops to install the agent. On bion-x299-gh the agent is installed to `D:\agent`. Install the agent as a service that runs as NETWORK SERVICE.