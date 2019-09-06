# STL Roadmap

This is an overview of what we're planning to work on, roughly prioritized.

* Migrate Bugs: We need to file a GitHub issue for each active bug in the STL's Microsoft-internal database.

* Migrate Todos: We need to file a GitHub issue for each "investigate this someday" todo that we've been tracking in Microsoft-internal documents.

* Build System: We need to extend our new CMake build system until it can completely replace our legacy build system.

* Tests: We need a new test harness for our test suites devcrt, tr1, and libcxx. (It may be possible to adapt an existing test harness for our purposes. Our tests are unusually concerned about being compiled with multiple compilers and multiple command lines.)

* Continuous Integration: We'll need to use GitHub Actions, Azure Pipelines, or something else.

* Contribution Guidelines: We need to write down all of the rules for STL development, like why our code is so `_Ugly`.

* Implement C++20 Features: That's why we're here, after all.

* Implement LWG Issues: We have a near-zero backlog of LWG issue resolutions to implement, and we'd like to keep it that way.

* Fix Bugs: Filing bugs is nice, but fixing them is nicer.

* Start vNext: We had a binary-incompatible branch named "WCFB02" in Team Foundation Version Control, where we accumulated significant overhauls and fixes. Due to time constraints, we didn't migrate it to Microsoft-internal MSVC git. Now we need to migrate this work to a branch of this repository, so we can resume those overhauls and accept more from the community.