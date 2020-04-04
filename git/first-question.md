# Pierwszy Merge Request

Zmiany do developa

| Krok | Komenda | Opis |
| :--- | :--- | :--- |
| 1 | **git checkout -b** _nowy-branch_ | Utwórz nowy branch dedykowany do Twoich zmian. Przykładowe nazwy: dev-WAR-3989, dev-calculatorFix |
| 2 | **git add .** | Dodanie zmian do staging. |
| 3 | **git commit -m** "_komunikat_" | Commit zmian do nowego brancha. Komunikat powinien zawierać numer zgłoszenia w JIRA i krotki opis zmian. `TIP: Commit'uj wielokrotnie. Dzięki temu łatwo cofnąć się do poprzedniej zmiany` |
| 4 | **git branch -u** _origin/develop_ | _Set an upstream branch for current branch._ Powiązanie nowego brancha z branchem z origin, w tym wypadku z origin/develop |
| 5 | **git pull --rebase** | _git pull runs **git fetch** with the given parameters and calls **git merge** to merge the retrieved branch heads into the current branch. With --rebase, it runs **git rebase** instead of git merge._ |
| 6 | **git push origin** _nowy-branch_ | Po rozwiązaniu ewentualnych konfliktów możesz wrzucić Twoją nową gałąź na origin. Uwaga: case-sensitive. |
| 7 | **Gitlab &gt; Create merge request** | Utwórz nowy merge request wskazując Tój nowy branch i branch docelowy. Upewnij się, że request zawiera wlaściwe zmiany. zaznacz opcję "Remove source branch". Submit -&gt; spowoduje wywołanie builda na Jenkinsie |

\(!\) Jeżeli zmiany są wprowadzane do hotfix, to po merge'u wykonaj jeszcze cherry-pick do developa - najlatwiej z poziomu gitlaba

| Problem? | Komenda | Opis |
| :--- | :--- | :--- |
| merge/rebase powodują konflikty? |  | Rozwiąż je w IntelliJ. Konflikty wyświetlają się na czerwono w zakładce "Version Control". Z menu kontekstowego wybierz Git &gt; Resolve conflicts. Pojawi się okno z trzema wersjami kodu - Twoją, z origina, a w środku z rezultatem merge'a. Zielone i niebieskie konflikty nie powodują problemów - kliknij "Apply non-conflicting". Czerwone wymagają ręcznej decyzji, który wprowadzić i który usunąć - edytuj Merge Result. |
| coś poszło źle? | git reset --hard HEAD~1 | Wycofanie zmian do poprzedniego commita. |
| gdzie jestem? | git status | Sprawdzenie stanu staging i working tree. |
| build failed | przyczyna: Sonar | Sprawdź błędy na sonarze i popraw kod zgodnie z zaleceniami. |
| poprawiłam kod, co dalej? |  | Ponownie skomituj zmiany:  1. **git commit --amend** \(jeżeli chcesz uzupełnić ten sam commit co poprzednio\)  2. **git push origin** _**nowy-branch**_ **-f** |
| wycofałam commity, zrobiłam nowy, co dalej? |  | git push origin _nowy-branch_ -f |

