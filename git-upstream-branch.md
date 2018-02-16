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



[https://longair.net/blog/2011/02/27/an-asymmetry-between-git-pull-and-git-push/](https://longair.net/blog/2011/02/27/an-asymmetry-between-git-pull-and-git-push/)

By default, `git push origin` will update branches on the destination **with one with the same name on the source**, _instead of using the association defined by_ `git branch --track`, which `git pull origin` would use.

Dalej jest wyjaśnione jak zachowają się te cztery komendy i dlaczego \(add-menu to nazwa nowego lokalnego brancha\):

1. git push github add-menu
2. git push github
3. git push
4. git push github HEAD

Pełna składnia **git push** to `git push <origin> <src>:<dst>`

Jeżeli brak &lt;dst&gt; to przyjmowana jest taka sama nazwa jak &lt;src&gt; i jeżeli brak takiej gałęzi remote, to jest dodawana.  
Jeżeli brak &lt;src&gt; to aktualizowane są wszystkie gałęzie remote o nazwach takich jak gałęzie lokal, ale nie są zakładane nowe.



