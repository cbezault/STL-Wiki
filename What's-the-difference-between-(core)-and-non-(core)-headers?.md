In our implementation, you'll see that some headers are annotated:

    // example standard header (core)

while others are only:

    // example standard header

without a `(core)` suffix. "core" refers to headers that can be `#include`'d into translation units without generating import declarations forcing linking with the standard libraries. The intent is to enable use of such headers in constrained operating environments like:

* the STL's own import libraries (where we merge functionality into the DLL's import lib to avoid needing to create a new DLL for some piece of functionality)
* kernel code
* Windows code that can't link with the STL
* enclave / SGX protected code

Generally, we want "compiler support" headers like `<type_traits>` to be in the core subset so that even constrained environments can get the "core speaking through `std::`" features. Core headers all start with `#include <yvals_core.h>` or another header that does so; other headers start with `#include <yvals.h>`.