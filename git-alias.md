zgodnie z opisem tutaj [https://stackoverflow.com/questions/31099564/git-alias-with-multiple-commands-and-arguments](https://stackoverflow.com/questions/31099564/git-alias-with-multiple-commands-and-arguments)

użyłam 'old [shell function technique](https://stackoverflow.com/a/3322412/354577)'

```
git config --global alias.zlib '!f() { git commit --amend && git push origin $1 -f; }; f'
```
inne aliasy (globalny .gitconfig znajduje się w c:/użytkownicy)
```
[alias]
	zlib = "!f() { git commit --amend && git push origin $1 -f; }; f"
	cleanup = !git branch --merged | egrep -v \"(^\\*|master|develop)\" | xargs git branch -d
	amend = !git add -A && git commit --amend --no-edit
	p = !git push origin $(git rev-parse --abbrev-ref HEAD)
```


