zawsze po rebase musisz wykonać push z force

git push -f origin &lt;branchname&gt;

Zwykły push zwróci komunikat w rodzaju:

`To gitlab.sigma.bestsa3.best.com.pl:sigma/sigma-core.git`

` ! [rejected]              dev-calculatorFix -> dev-calculatorFix (non-fast-forward)`

`error: failed to push some refs to 'git@gitlab.sigma.bestsa3.best.com.pl:sigma/sigma-core.git'`

`hint: Updates were rejected because the tip of your current branch is behind`

`hint: its remote counterpart. Integrate the remote changes (e.g.`

`hint: 'git pull ...') before pushing again.`

`hint: See the 'Note about fast-forwards' in 'git push --help' for details.`

patrz [https://git-scm.com/book/en/v1/Git-Branching-Rebasing](https://git-scm.com/book/en/v1/Git-Branching-Rebasing)

Rebasing changes the SHA-1 hashes of these commits so to Git they look like new commits,

Dlatego, że Twoje commity wchodzą na wierzch commitów rebase'owanych

Ponieważ zmienia się parent commit, to i SHA Twoich commitów zostaje zmienione







