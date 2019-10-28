We've implemented the Standard's feature-test macros, which are the best way to determine whether a feature is supported by your current combination of compiler vendor, compiler version, library vendor, library version, and build settings. However, it can occasionally be useful to query the library version directly. We provide an implementation-specific macro `_MSVC_STL_UPDATE` defined in the STL's central internal header [`yvals_core.h`](https://github.com/microsoft/STL/blob/master/stl/inc/yvals_core.h); users should include `<version>` or any other Standard header to get this macro. This macro follows the year-month format of Standard feature-test macros, but isn't related to any of them. We simply intend to update the value of `_MSVC_STL_UPDATE` every month, so when a Visual Studio update ships, it captures a new value.

Here are the historical values of this macro, verified from actual installations of released (non-preview) Visual Studio updates:

Toolset Version | `_MSVC_STL_UPDATE`
-----:|:-----
19.11 | none
19.12 | `201709`
19.13 | `201711`
19.14 | `201803`
19.15 | `201806L`
19.16 | `201809L`
19.20 | `201811L`
19.21 | `201903L`
19.22 | `201905L`
19.23 | `201906L`
