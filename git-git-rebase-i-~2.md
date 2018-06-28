Otwiera rebase interactive mode dla 2 ostatnich commitów

\_@ \_alone is a shortcut for `HEAD (`ięcej o symbolach [https://git-scm.com/docs/gitrevisions](https://git-scm.com/docs/gitrevisions)\)

**Rebasing is the process of moving or combining a sequence of commits to a new base commit.**

[https://nathanleclaire.com/blog/2014/09/14/dont-be-scared-of-git-rebase](https://nathanleclaire.com/blog/2014/09/14/dont-be-scared-of-git-rebase)

Może zrobić różne zmiany:

* change “pick” on those commits’ lines to “squash”. Commits with “squash” on consecutive lines will be combined into one
* to quickly drop the commits from your new branch just delete the lines for the commit\(s\) in the interactive rebase prompt

* jeżeli wybierzesz edit to będzie się zatrzymywał przed rebasem każdego commita: just change`pick`to`edit`for the commits in question, and do a`git commit --amend -s`\(to sign a commit\) and`git rebase --continue`for each commit.

Re-writing history with `git rebase`, as you have seen, is fun \_and \_useful, but once history hits remotes that other people are using it should be considered canon and it should almost never be changed. So, if you rebase, make sure not to muck with \_other people’s \_history and commits on accident. Likewise, if you force push, NEVER EVER force push to a remote where other people are working

[https://git-scm.com/docs/git-rebase](https://git-scm.com/docs/git-rebase)

By replacing the command "pick" with the command "**edit**", you can tell _git rebase _**to stop after applying that commit**, so that you can edit the files and/or the commit message, amend the commit, and continue rebasing `git rebase --continue.`

If you just want to** edit the commit message for a commit**, replace the command "pick" with the command "**reword**".

To **drop a commit**, replace the command "pick" with "**drop**", **or **just** delete the matching line**.

If you want to **fold two or more commits into one**, replace the command "pick" for the second and subsequent commits with "**squash**" or "**fixup**". If the commits had different authors, the folded commit will be attributed to the author of the first commit. The suggested commit message for the folded commit is the concatenation of the commit messages of the first commit and of those with the "squash" command, but omits the commit messages of commits with the "fixup" command.

Dodatkowa opcja --onto

**git rebase --onto &lt;newbase-treeish&gt; &lt;oldbase-treeish&gt; &lt;treeish&gt;**

odepnij treeish od bazy old i przypnij do new

Przykład:

```
 E---F---G---H---I---J  topicA
```

```
git rebase --onto topicA~5 topicA~3 topicA
```

```
E---H'---I'---J'  topicA
```



