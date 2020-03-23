# Always

* Proofread the commit message.
  * The title should be clear, i.e. suitable for scanning in `git log`, `gitk`, etc.
  * The body can be empty (i.e. the PR number records what happened and why), or it can contain a small or large amount of additional information. However, it shouldn't be a messy concatenation of commit messages during development (e.g. "fixed typo", "code review feedback", etc.).
  * When [closing issues using keywords](https://help.github.com/en/github/managing-your-work-on-github/closing-issues-using-keywords), remember that the Words Of Power are important and they must be repeated when closing multiple issues.
  * Double-check all numbers (e.g. paper numbers and issue numbers) to catch common mistakes like reversing digits.
* Thank the contributor, especially if they're a first-time contributor! 😸

# When Closing Issues (Bugs, Enhancements, Features, LWG)

* In addition to closing the issue, tag it as `fixed` (and remove `work in progress` if that was present). Leave the other tags unchanged. We use `fixed` to mark issues that were solved via commits, as opposed to being `resolved` without a commit.
* Update the wiki's [Changelog](https://github.com/microsoft/STL/wiki/Changelog).

# When Adding Features (Or LWG Issues)

* Microsoft-internal: Update [stl.xlsx](https://microsoft.sharepoint.com/:x:/t/DD_VC/EVoxm5Q8dsNKiQrmJx79VEcBn8TQMH2k5Lf9uSVj-kRWig?e=stjtv6) or [lwg.xlsx](https://microsoft.sharepoint.com/:x:/t/DD_VC/EY2TKWJxBGpAhbRrmQIRtmoB6jmz7tSWlSatScneQlwkoQ?e=nHdQqR). (Note to contributors: these spreadsheets contain the same information as our `cxx20` and `lwg` tagged issues; Excel simply provides an easy-to-scan dashboard.)
  * Change the `Status` filter to display `patch` papers; restore this when you're done.
  * Change the `Status` from `missing` to the release that this will ship in. (Note that we update the `Status` for `patch` papers, but leave their `Notes`, `Dev`, `GitHub`, and `User Story` columns as saying `patch`.)
  * Update the `Notes`. We use `[GH]` for GitHub contributors and `[14]` (sometimes `[17]`) for unconditional features.
  * Record the `Dev`. This is a GitHub or Microsoft username. It should be hyperlinked to the GitHub PR that was merged.
  * Cut and paste the updated rows to sort them by their updated `Status` (followed by `Paper`, except that we try to group patches by their primary paper, so this is a manual sort).
  * Note: Certain copy-paste operations seem to clutter up the extensive Conditional Formatting, but cutting-and-pasting rows never seems to be harmful.
