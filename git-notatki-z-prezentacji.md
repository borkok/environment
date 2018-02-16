**Stronka do nauki gita:**  
[learngitbranching.js.org](https://learngitbranching.js.org/?NODEMO)  
   \($ git fakeTeamwork\)

**Rodzaje obiektów przechowywane w git:**  
pliki=blob  
folder\(struktura\)=tree \(ma w treści SHA do plików zawartych w folderze\)  
commit  
tag  
branch

**Przykładowy scenariusz z rebasem**  
1. git checkout dev-1  
2. git fetch  
3. git rebase origin/master \`dokleja commity z dev-1 do origin/master; ładniej wygląda, nie ma commitów mergowych, zostawiam historię całą sprzed rebase \(merge robi tylko jeden commit, rebase przenosi całą historię, ew. konflikty rozwiązujesz krok po kroku \(każdy commit po kolei\), nie jeden wielki merge z wielką listą konfliktów\)  
4. git push

**Inne komendy:**  
git rebase develop -i `można wskazać, które commity biorę (pick)`

git checkout `Nadpisze zmiany w katalogu roboczym. Updates files in the working tree to match the version in the index or the specified tree.`  
git checkout `<branch>` `To prepare for working on <branch>, switch to it by updating the index and the files in the working tree, and by pointing HEAD at    the branch. Local modifications to the files in the working tree are kept, so that they can be committed to the <branch>.`

