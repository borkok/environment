# GIT HEAD~2 vs HEAD^2

[http://www.paulboxley.com/blog/2011/06/git-caret-and-tilde](http://www.paulboxley.com/blog/2011/06/git-caret-and-tilde)

`ref~`is shorthand for`ref~1`and means the commit's first parent.`ref~2`means the commit's first parent's first parent.`ref~3`means the commit's first parent's first parent's first parent. And so on.

`ref^`is shorthand for`ref^1`and means the commit's first parent. But where the two differ is that`ref^2`means the commit's _**second parent**_ \(remember, commits can have two parents when they are a _merge_\).

The ^ and ~ operators can be combined.

