This repo supports [custom autolinks](https://help.github.com/en/articles/autolinked-references-and-urls), which work in GitHub conversations like issues and pull requests, but not the repo's own files. Anyone can use them simply by mentioning a special prefix, followed by a number.

# Examples

|            Pattern | Notes | Example |
|--------------------|-------|---------|
| DevCom-&lt;num&gt; | Developer Community bugs     | [DevCom-724444](https://developercommunity.visualstudio.com/content/problem/724444/meow.html) |
| LLVM-&lt;num&gt;   | Clang/LLVM bugs              | [LLVM-41915](https://bugs.llvm.org/show_bug.cgi?id=41915) |
| LWG-&lt;num&gt;    | Library Working Group issues | [LWG-3080](https://cplusplus.github.io/LWG/issue3080) |
| WG21-N&lt;num&gt;  | WG21 N-numbered documents    | [WG21-N4190](https://wg21.link/N4190) |
| WG21-P&lt;num&gt;  | WG21 P-numbered proposals    | [WG21-P1209](https://wg21.link/P1209) |

Note that GitHub's custom autolink syntax doesn't support R-numbered revisions, so you'll need to use https://wg21.link manually if you want to cite [P0896R0](https://wg21.link/P0896R0) versus [P0896R4](https://wg21.link/P0896R4).

# Microsoft-internal

We also have custom autolinks to Microsoft-internal bug databases, like VSO-&lt;num&gt;, OS-&lt;num&gt;, and ArchivedOS-&lt;num&gt;.