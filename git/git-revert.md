# GIT revert

[https://git-scm.com/docs/git-revert](https://www.gitbook.com/book/borkok/srodowisko-programisty/edit#)

\_git revert \_is used to record some new commits to reverse the effect of some earlier commits \(often only a faulty one\). If you want to throw away all uncommitted changes in your working directory, you should see [git-reset\[1\]](https://git-scm.com/docs/git-reset), particularly the`--hard`option. If you want to extract specific files as they were in another commit, you should see [git-checkout\[1\]](https://git-scm.com/docs/git-checkout), specifically the`git checkout <commit> -- <filename>`syntax. Take care with these alternatives as both will discard uncommitted changes in your working directory.

`git revert HEAD~3`

Revert the changes specified by the fourth last commit in HEAD and create a new commit with the reverted changes.

`git revert -n master~5..master~2`

Revert the changes done by commits from the fifth last commit in master \(included\) to the third last commit in master \(included\), but do not create any commit with the reverted changes \(-n option\). The revert only modifies the working tree and the index.

