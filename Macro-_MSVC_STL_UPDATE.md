We've implemented the Standard's feature-test macros, which are the best way to determine whether a feature is supported by your current combination of compiler vendor, compiler version, library vendor, library version, and build settings. However, it can occasionally be useful to query the library version directly. We provide an implementation-specific macro `_MSVC_STL_UPDATE` defined in the STL's central internal header [`yvals_core.h`](https://github.com/microsoft/STL/blob/master/stl/inc/yvals_core.h); users should include `<version>` or any other Standard header to get this macro. This macro follows the year-month format of Standard feature-test macros, but isn't related to any of them. We simply intend to update the value of `_MSVC_STL_UPDATE` every month, so when a Visual Studio update ships, it captures a new value.

Here are the historical values of this macro, verified from actual installations of released (non-preview) Visual Studio updates:

Toolset Version | Visual Studio | `_MSVC_STL_UPDATE`
-----:|:-----|:-----
19.11 and earlier | earlier | none
19.12 | VS 2017 15.5 | `201709`
19.13 | VS 2017 15.6 | `201711`
19.14 | VS 2017 15.7 | `201803`
19.15 | VS 2017 15.8 | `201806L`
19.16 | VS 2017 15.9 | `201809L`
19.20 | VS 2019 16.0 | `201811L`
19.21 | VS 2019 16.1 | `201903L`
19.22 | VS 2019 16.2 | `201905L`
19.23 | VS 2019 16.3 | `201906L`
19.24 | VS 2019 16.4 | `201909L`