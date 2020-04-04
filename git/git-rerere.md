# GIT rerere

Reuse recorded resolution of conflicted merge

In a workflow employing relatively long lived topic branches, the developer sometimes needs to resolve the same conflicts over and over again until the topic branches are done

Załóżmy, że pracujesz na feature branchu. Co jakiś czas "odświeżasz" do robiąc pull z developa do feature brancha. When your topic branch is long-lived, however, your topic branch would end up having many such "Merge from master" commits on it, which would unnecessarily clutter the development history. Readers of the Linux kernel mailing list may remember that Linus complained about such too frequent test merges when a subsystem maintainer asked to pull from a branch full of "useless merges".

As an alternative, to keep the topic branch clean of test merges, you could blow away the test merge - po przetestowaniu zrób `git reset --hard HEAD^`, and keep building on top of the tip before the test merge.

Ale potem jak już ostatecznie chcesz domergować do developa \(mastera\) to musisz rozwiązać jeszcze raz wszystkie konflikty, które rozwiązałaś już raz robiąc w "testowy" merge.

Zamiast tego możesz włączyć rerere:

Add it to your global config to enable it for all projects: `git config --global rerere.enabled true`

Od tego momentu  `git merge` automatically invokes `git rerere` upon exiting with a failed automerge and `git rerere` records the hand resolve when it is a new conflict, or reuses the earlier hand resolve when it is not. `git commit` also invokes `git rerere` when committing a merge result. Tak samo `git rebase`.

{% embed url="https://git-scm.com/docs/git-rerere" %}

