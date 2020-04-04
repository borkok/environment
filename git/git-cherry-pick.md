# GIT cherry-pick

[https://stackoverflow.com/questions/9339429/what-does-cherry-picking-a-commit-with-git-mean](https://stackoverflow.com/questions/9339429/what-does-cherry-picking-a-commit-with-git-mean)

**Cherry picking in git means to choose a commit from one branch and apply it onto another.**

This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.

only changes made by that commit are applied

[https://git-scm.com/docs/git-cherry-pick](https://git-scm.com/docs/git-cherry-pick)

`git cherry-pick master~4 master~2`

Apply the changes introduced by the fifth and third last commits pointed to by master and create 2 new commits with these changes.

`git cherry-pick master`

Apply the change introduced by the commit at the tip of the master branch and create a new commit with this change.

The command git cherry-pick commit applies the changes introduced by the named commit on the current branch. It will introduce a new, distinct commit.

**Strictly speaking, using git cherry-pick doesn’t alter the existing history within a repository; instead, it adds to the history.** As with other Git operations that introduce changes via the process of applying a diff, you may need to resolve conflicts to fully apply the changes from the given commit. The command git cherry-pick is typically used to introduce particular commits from one branch within a repository onto a different branch. A common use is to forward- or back-port commits from a maintenance branch to a development branch.

