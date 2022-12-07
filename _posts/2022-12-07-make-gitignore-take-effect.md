---
title: "Make gitignore take effect"
date: 2022-12-07
---
You realise there are files you don't want git to track but they already tracked. 

You added a new line
to `.gitignore`, e.g. `*.aux`. 
However you still find the file already tracked by git are still there 
(to be precise, in git staging).

How do you make the change in `.gitignore` take effect?

If there is only one or two files to un-track, simply:
```shell
git rm --cached <file_to_untrack>
```

If there are many files to un-track, consider
```shell
git rm -rf --cached .
git add .
```
The first step un-tracks all the files and the second adds back al the files that are not git-ignored.

Key take-away:
Use `git rm --cached <file_name>`to make git un-track a file.

What if we don't give `git rm` the `--cached` parameter?

That's a powerful command. 
It deletes the file from directory AND makes git un-track the file at the same time.
git actually requires providing `-f` flag when using this, i.e.
`git rm -f <file_name>` would work.


References:
[1]: https://sidecode.io/dev-blog/making-gitignore-to-take-effect-gitignore-is-not-working/
[2]: https://careerkarma.com/blog/git-rm/#:~:text=The%20Git%20rm%20%E2%80%93cached%20flag,index%20tracking%20your%20Git%20project.
