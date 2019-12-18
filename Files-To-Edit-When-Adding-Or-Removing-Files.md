The following are lists of files that need to be updated whenever we add a header file, source file, or binary to the STL.

* "Headers" are consumed directly or indirectly by users. Headers can be **public**, which means we intend for customers to include them directly and we consider their names and contents contractual, like `<vector>`. We also have private headers which are internal implementation details, like `<xutility>`.
* "Sources" are compiled into msvcp140.dll/libcpmt.lib/etc. For example, filesystem.cpp and xmath.h. 
* "Binaries" are arch/flavor-specific DLLs (and their PDBs). For example, bin\i386\onecore\msvcp140_codecvt_ids.dll and bin\i386\msvcp140_codecvt_ids.i386.onecore.pdb.

Adds, renames, and deletes are handled identically, except that the IDE's list of extensionless headers should generally never stop mentioning names.

## Edits in this GitHub repository

* **stl/CMakeLists.txt**

  When adding *headers* or *sources*, so that the build system picks them up.

* **stl/msbuild/stl_base/stl.files.settings.targets**

  When adding *sources*, so that the legacy build system picks them up.

* **stl/inc/__msvc_all_public_headers.hpp**

  When adding *public headers*, so that customers who are using this header as a way to test all the standard library headers are actually testing all the standard library headers.

## Edits in the MSVC team's internal repository

Ask an STL maintainer to do this for you if you change the set of files in a pull request.

When editing any installers related files, we need to remember to notify the **vctowner** alias. The folks on that alias are responsible for editing the mechanism by which Visual Studio is built with new bits.

* **src/vctools/crt/lkgsync/updatelkgmanifest.cmd**

  When adding *headers* or *sources*, run this to update scripts used for synchronizing libraries team code into the Windows tree.

* **src/SetupPackages/swix/VisualCpp/crt.headers/files.swr**

  Update this list to get new *headers* picked up by the Visual Studio installers.

* **src/SetupPackages/swix/VisualCpp/crt.source/files.swr**

  Update this list to get new *sources* picked up by the Visual Studio installers (for example, `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Tools\MSVC\14.24.28314\crt\src`).

* **src/vctools/crt/copy_crt/copy_crt.nativeproj**

  When adding *headers*, this is used by parts of the build that consume the "live" headers.

* **src/qa/VC/Libs/devcrt/tests/CPP/include_each_header_alone_matrix.lst**

  When adding *public headers*, this test makes sure each header can be included by itself and that we don't have any accidental internal dependencies.

* **src/vctools/StdIfc/modules/core.cpp**

  When adding **Standard** *public headers*, add to this list to ensure they're included in the 'experimental modules' support.

* **src/vctools/crt/managed/msvcurt.settings.targets**

  When adding *sources*, this is used by our build system (for /clr:pure's msvcurt*.lib). 

* **src/vctools/crt/msdl_publishing/msdl_publishing.xml**

  When adding *binaries* for which we want to publish private symbols and binaries to the public symbol server, we need to add each architecture and flavor of the DLL and its PDB to this file under the corresponding architecture. We need to run `msdl_publishing/checkmsdlxml.cmd` to ensure edits are reflected in the local build.

## Edits in the Visual Studio repository

Ask an STL maintainer to do this for you if you change the set of files in a pull request.

* **src/vc/designtime/pkg/src/VC_Pkg_Core_Registration.pkgdef**

  When adding **extensionless** *headers*, this makes the Visual Studio IDE recognize them as C++. Technically we must mark private headers here if they are extensionless, but going forward we've been giving private headers a .h extension so that this list need not be modified. [Microsoft-internal link.](https://devdiv.visualstudio.com/DevDiv/_git/VS?path=%2Fsrc%2Fvc%2Fdesigntime%2Fpkg%2Fsrc%2FVC_Pkg_Core_Registration.pkgdef&version=GBmaster)