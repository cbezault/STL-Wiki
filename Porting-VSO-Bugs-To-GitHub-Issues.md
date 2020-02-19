We're working on porting all of the STL bugs in our Microsoft-internal VSO database to GitHub issues. Here's the process:

# GitHub Issue

1. The GitHub issue needs a good title. It shouldn't contain `[Feedback]` or `[VSFeedback]`. Follow README.md's guidance:

> We prefer "`<header_name>`: Short description of your issue". You don't usually need to
mention `std::` or C++. For example, "`<type_traits>`: `is_cute` should be true for `enum class FluffyKittens`".

2. The GitHub issue needs a good test case and/or explanation, suitable for contributors who are skilled and eager to help, but who aren't deeply familiar with the context and history. This often requires a fair amount of work.

3. The GitHub issue should take advantage of source code quoting whenever possible, using [permalinks](https://help.github.com/en/github/managing-files-in-a-repository/getting-permanent-links-to-files) to code snippets.

4. The GitHub issue needs one main tag, plus optional tags. Common examples:

    * Main tags:
        * `bug` - Correctness.
        * `performance` - Runtime speed.
        * `throughput` - Compiletime speed.
        * `documentation` - Involves documentation/comments only.
        * `test` - Involves test code only.
        * `enhancement` - All other improvements.
    * Optional tags:
        * `decision needed` - The MSVC STL team needs to choose something before working on this.
        * `good first issue` - Appropriate for reasonably small issues that are simple to understand and fix. Should have an especially clear explanation for contributors who are fairly new to GitHub and C++ Standard Library development.
        * `help wanted` - Appropriate for issues (regardless of size) where the MSVC STL team needs additional expertise, not just time.
        * `info needed` - We need a complete test case or other information.
        * `vNext` - Breaks binary compatibility.

5. The GitHub issue needs cross-references:

    * "Also tracked by Microsoft-internal VSO-number." or
    * "Also tracked by DevCom-number and Microsoft-internal VSO-number."

# VSO Bug

6. The VSO bug needs to be tagged `STL-GitHub` which allows us to distinguish what has been ported from what remains to be ported.

7. The VSO bug needs to link to the GitHub issue. Just paste the URL in a comment.

# Open Questions

Most VSO bugs should be 1-to-1 ported to GitHub issues. There are a few mega-bug-areas like `regex` and `get_time` where we might want to consolidate things, but we need to avoid discarding any unique test cases.