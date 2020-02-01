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
- [x] [WG21 Belfast Meeting](https://wg21.link/n4814).
- [x] Merged 7 C++20 features:
  - P0340R3 [#284](https://github.com/microsoft/STL/pull/284) SFINAE-Friendly `underlying_type`
  - P0553R4 [#310](https://github.com/microsoft/STL/pull/310) `<bit>` Rotating And Counting Functions
  - P0556R3 [#310](https://github.com/microsoft/STL/pull/310) `<bit>` `ispow2()`, `ceil2()`, `floor2()`, ~~`log2p1()`~~ `bit_length()`
  - P0631R8 [#261](https://github.com/microsoft/STL/pull/261) `<numbers>` Math Constants
  - P0738R2 [#246](https://github.com/microsoft/STL/pull/246) `istream_iterator` Cleanup
  - P1209R0 [#236](https://github.com/microsoft/STL/pull/236) `erase_if()`, `erase()`
  - P1612R1 [#305](https://github.com/microsoft/STL/pull/305) Relocating `endian` To `<bit>`

# December 2019
- [x] Merged C++20 features:
  - P0595R2 [#353](https://github.com/microsoft/STL/pull/353) `is_constant_evaluated()`
  - P1690R1 [#341](https://github.com/microsoft/STL/pull/341) Refining Heterogeneous Lookup For Unordered Containers
  - P1902R1 [#353](https://github.com/microsoft/STL/pull/353) Missing Feature-Test Macros 2017-2019

# January 2020
- [x] Deprecate `std::rel_ops` [#402](https://github.com/microsoft/STL/pull/402)
- [x] Significantly improved performance of `string + null terminated` and `null terminated + string` `operator+` overloads in `<string>`. (part of [#467](https://github.com/microsoft/STL/pull/467))
- [x] Merged C++20 features:
  - P0122R7 [#142](https://github.com/microsoft/STL/pull/142) `<span>`
  - P0202R3 [#425](https://github.com/microsoft/STL/pull/425) `constexpr` For `<algorithm>` And `exchange()`
  - P0357R3 [#393](https://github.com/microsoft/STL/pull/393) Supporting Incomplete Types In `reference_wrapper`
  - P0879R0 [#425](https://github.com/microsoft/STL/pull/425) `constexpr` For Swapping Functions
  - P0883R2 [#390](https://github.com/microsoft/STL/pull/390) Fixing Atomic Initialization
  - P1006R1 [#397](https://github.com/microsoft/STL/pull/397) `constexpr` For `pointer_traits<T*>::pointer_to()`
  - P1165R1 [#467](https://github.com/microsoft/STL/pull/467) Consistently Propagating Stateful Allocators In `basic_string`'s `operator+()`
  - P1645R1 [#399](https://github.com/microsoft/STL/pull/399) `constexpr` For `<numeric>` Algorithms

# February 2020
- [ ] [WG21 Prague Meeting](https://wg21.link/n4817).
- [X] Merged C++20 features:
  - P1423R3 [#470](https://github.com/microsoft/STL/pull/470) `char8_t` Backward Compatibility Remediation

# Future
- [ ] `devcrt` test suite running in PRs.
- [ ] `tr1` test suite running in PRs.
- [ ] `libcxx` test suite running in PRs.
- [ ] Bring remaining build system components online so that we can shut down the old internal build system.
- [ ] Enable automatic ingestion of GitHub changes into Visual Studio.