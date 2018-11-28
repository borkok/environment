zgodnie z opisem tutaj [https://stackoverflow.com/questions/31099564/git-alias-with-multiple-commands-and-arguments](https://stackoverflow.com/questions/31099564/git-alias-with-multiple-commands-and-arguments)

użyłam 'old [shell function technique](https://stackoverflow.com/a/3322412/354577)'

```
git config --global alias.zlib '!f() { git commit --amend && git push origin $1 -f; }; f'
```



