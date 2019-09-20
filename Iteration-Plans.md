# September
- [x] Announce this repo at [CppCon 2019](https://cppcon.org/).
- [x] Add initial documentation: readme, license, and roadmap.
- [x] Add initial CMake build scripts for Desktop-only msvcp.
- [ ] Investigate test harness solutions, either building our own to more closely match the internal system in a reasonable way, or using libcxx's `lit`.

# October
- [ ] Bring remaining build system components online so that we can shut down the old internal build system.
- [ ] Begin auditing and adding test case source files from the `devcrt` test harness.
- [ ] Investigate continuous integration options, like GitHub Actions or Azure Pipelines.

# November
- [ ] [WG21 Belfast Meeting](https://wg21.link/n4814).

# Future
- [ ] Builds running in PRs.
- [ ] `devcrt` test harness running in PRs.
- [ ] `tr1` test harness running in PRs.
- [ ] `libcxx` test harness running in PRs.
- [ ] Enable automatic ingestion of GitHub changes into Visual Studio.