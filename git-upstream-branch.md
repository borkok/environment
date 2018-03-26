**Uwaga! Można mieć inny upstream dla merge i inny dla push. **

Po wykonaniu komend z "Pierwszy Merge Request" stan nowej gałęzi jest taki:

`$ git remote show origin`

....

Local branches configured for 'git pull':

```
dev-calculatorFix merges with remote develop

develop           merges with remote develop
```

_\(to powstało w wyniku **git branch -u origin/develop\)**_

Local refs configured for 'git push':

```
dev-calculatorFix pushes to dev-calculatorFix \(up to date\)

develop           pushes to develop           \(local out of date\)
```

_\(to powstało w wyniku **git push origin &lt;nazwa&gt;**\)_

**W pliku .config **zapisana jest taka konfiguracja:

\[branch "dev-calculatorFix"\]

```
remote = origin  
merge = refs/heads/develop
```

Szczegółowo wyjaśnione to jest tutaj: [https://longair.net/blog/2011/02/27/an-asymmetry-between-git-pull-and-git-push](https://longair.net/blog/2011/02/27/an-asymmetry-between-git-pull-and-git-push/)/

"By default, `git push origin` will update branches on the destination **with one with the same name on the source**, _instead of using the association defined by_ `git branch --track`, which `git pull origin` would use."

Dalej jest wyjaśnione jak zachowają się te cztery komendy i dlaczego \(add-menu to nazwa nowego lokalnego brancha\):

1. **git push github add-menu** If:&lt;dst&gt; is omitted, the same ref as &lt;src&gt; will be updated.
   So the command is equivalent togit push github add-menu:add-menu, which will create a new branch calledadd-menuon GitHub

2. **git push github **for every branch that exists on the local side, the remote side is updated if a branch of the same name already exists on the remote side. Czyli nie założy nowego brancha
3. **git push** Works like git push &lt;remote&gt;, where &lt;remote&gt; is the current branch’s remote \(or origin, if no remote is configured for the current branch\). Czyli tak samo jak w pkt. 2
4. **git push github HEAD **A handy way to push the current branch to the same name on the remote.
   In other words, in this example, that will end up being the same as _git push github add-menu:add-menu_, again creating an add-menu branch in the remote repository

Pełna składnia **git push** to `git push <origin> <src>:<dst>`

Jeżeli brak &lt;dst&gt; to przyjmowana jest taka sama nazwa jak &lt;src&gt; i jeżeli brak takiej gałęzi remote, to jest dodawana.  
Jeżeli brak &lt;src&gt; to aktualizowane są wszystkie gałęzie remote o nazwach takich jak gałęzie lokal, ale nie są zakładane nowe.

