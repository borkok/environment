**git config**  
git config --global user.name "Kinga Borkowska"  
git config --global user.email "kinga@gmail.com"

**git help**

**git init**

**git add .**  
git add file.txt

**git commit -am "commit message"**  
git commit --amend `zmienia ostatni commit`

**git log**  
git log --oneline -5  
git log --grep=`<regexpression>`  
git log --since="2012-06-20" --until="2012-07-03"  
git log 293848ad..adfe32e444  
git log --graph  
git log --oneline --graph --all --decorate

**git show** ad34ee34f

**git status**

**git diff**  
git diff --staged  
git diff --color-words  
git diff 223838..939383  
git diff treeishA..treeishB

**git rm**      `usuwa plik`

**git mv** `zmienia nazwę pliku`

**git checkout** `<nazwa-brancha>`  `nie pozwoli Ci na zmianę brancha, jeżeli masz nieskomitowane zmiany w working tree, chyba że użyjesz opcji -f / --force`
git checkout -- <nazwa pliku>  `przywraca wersję pliku z obecnego stanu w local repository`
git checkout -- .   `discard changes in working dir`  
git checkout `<SHA wcześniejszego commita>` --`<nazwa pliku>`  `wrzuca tylko do staging, nie do working dir`  


**git reset** HEAD `<nazwa pliku>` `opposite of git add <paths>, resets the index entries for all <paths> to their state at <tree-ish>. (It does not affect the working tree or the current branch.)`
git reset --soft      `przesuwa HEAD na wskazany SHA, domyślnie ostatni commit`
git reset --mixed     `domyślny, zmienia staging, nie zmienia working`
git reset --hard      `destructive, zmienia też working dir`

**git revert** `<SHA commit>` `git revert is used to record some new commits to reverse the effect of some earlier commits (often only a faulty one).`

If you want to throw away all uncommitted changes in your working directory, you should see `git-reset`, particularly the `--hard option`. If you want to extract specific files as they were in another commit, you should see `git-checkout`, specifically the `git checkout <commit> -- <filename>` syntax. Take care with these alternatives as both will discard uncommitted changes in your working directory.

**git clean -f**  `removes all untracked files`
git clean -n `tylko je wypisuje`

**plik .gitignore**  `tu wypisz pliki, których ma git nie śledzić`
git config --global core.excludesfile ~/.gitignore\_global

**plik .gitkeep** `pusty plik dodany tylko po to, aby git utrzymywał ten pusty folder`

**git ls-tree HEAD**

**git branch** `listuje lokalne branche`
git branch -r
git branch -a
git branch `<nazwa>`  `tworzy nowy branch`
git branch --move oldname newname
git branch --delete `<nazwa>`

**git stash save**  `save our changes + runs git reset hard HEAD`
git stash list
git stash show -p stash@{0}        `pokazuje diff bransh vs stash`
git stash pop        `wyciąga ze stasha i próbuje zmergować z working dir`
git stash apply        `kopiuje ze stasha`
git stash drop stash@{0}
git stash clear

**git remote add origin** [https://github.com/borkok/skyscrapers.git](https://github.com/borkok/skyscrapers.git)
git remote add `alias` `url`
git remote rm origin

**git push** -u origin master 

**git clone URL** \[opcj. nazwa\_folderu\]

**git fetch**   `1. fetch often; 2. fetch before work (every morning); 3. fetch before push (1. fetch 2. merge 3. push)`

**git merge** origin/master
git merge --abort    \(jest konflikt i nie chcesz kontynuować merge’a\)

**git pull** = git fetch + git merge

git branch nowy\_branch origin/nowy\_branch
git checkout -b nowy\_branch origin/nowy\_branch `utwórz nowy branch jako kopię brancha z origin`

git push origin --delete `<nazwa_brancha>`

