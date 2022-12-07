---
title: "Make gitignore take effect"
date: 2022-12-07
---
You look at your git staging area and
realise there are files you don't want git to track 
but they are already tracked. Let's say the file is `1.aux`.

You added a new line
to `.gitignore`, e.g. `*.aux` to make git ignore all `.aux` files.
However, you find `1.aux` still tracked by git.  

How do you make the change in `.gitignore` take effect?

If there is only one or two files to un-track, simply:
```shell
git rm --cached <file_to_untrack>
```
to instruct git to un-track a file.


If there are many files to un-track, consider
```shell
git rm -rf --cached .
git add .
```
The first step un-tracks all the files and the second adds back al the files that are not git-ignored.

Note:
What if we don't give `git rm` the `--cached` parameter?

That's a powerful command. 
It deletes the file from directory AND makes git un-track the file at the same time.
git actually requires providing `-f` flag when using this, i.e.
`git rm -f <file_name>` would work.


References:

[1]: [sidecode.io](https://sidecode.io/dev-blog/making-gitignore-to-take-effect-gitignore-is-not-working/)

[2]: [careerkarma.com](https://careerkarma.com/blog/git-rm/#:~:text=The%20Git%20rm%20%E2%80%93cached%20flag,index%20tracking%20your%20Git%20project.)
