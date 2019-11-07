# September 2019
- [x] Announce this repo at [CppCon 2019](https://cppcon.org/).
- [x] Add initial documentation: readme, license, and roadmap.
- [x] Add initial CMake build scripts for Desktop-only msvcp.
- [x] Investigate continuous integration options, like GitHub Actions or Azure Pipelines. (Chose Azure Pipelines.)
- [x] Builds running in PRs.
- [x] Merged 4 C++20 features:
  - P0325R4 [#135](https://github.com/microsoft/STL/pull/135) `to_array()`
  - P0439R0 [#124](https://github.com/microsoft/STL/pull/124) `enum class memory_order`
  - P1227R2 [#130](https://github.com/microsoft/STL/pull/130) Signed `std::ssize()`
  - P1357R1 [#127](https://github.com/microsoft/STL/pull/127) `is_bounded_array`, `is_unbounded_array`

# October 2019
- [x] Investigate test harness solutions, either building our own to more closely match the internal system in a reasonable way, or using libcxx's `lit`. (Chose to build our own.)
- [x] Begin auditing test case source files from the `devcrt` and `tr1` test suites.
- [x] Implemented [Custom Autolinks](https://github.com/microsoft/STL/wiki/Custom-Autolinks) in this repo.
- [x] Merged 4 C++20 features:
  - P0356R5 [#158](https://github.com/microsoft/STL/pull/158) `bind_front()`
  - P0655R1 [#201](https://github.com/microsoft/STL/pull/201) `visit<R>()`
  - P0767R1 [#179](https://github.com/microsoft/STL/pull/179) Deprecating `is_pod`
  - P0966R1 [#176](https://github.com/microsoft/STL/pull/176) `string::reserve()` Should Not Shrink

# November 2019
- [ ] [WG21 Belfast Meeting](https://wg21.link/n4814).
- [ ] `devcrt` test suite running in PRs.
- [ ] `tr1` test suite running in PRs.
- [x] Merged C++20 features:
  - P0738R2 [#246](https://github.com/microsoft/STL/pull/246) `istream_iterator` Cleanup
  - P1209R0 [#236](https://github.com/microsoft/STL/pull/236) `erase_if()`, `erase()`

# Future
- [ ] `libcxx` test suite running in PRs.
- [ ] Bring remaining build system components online so that we can shut down the old internal build system.
- [ ] Enable automatic ingestion of GitHub changes into Visual Studio.