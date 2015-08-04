+++
date = "2015-03-12T22:14:51+02:00"
title = "Finding files in git log"

+++

Show all git log entries that concern a certain (existing or non-existing) file path:
```bash
git log --all -- <path>
```
`path` is a git `pathspec` that can contain `*`s and `?`s ([more info here](http://git-scm.com/docs/gitglossary))

Add a modifier like `--stat`, `--name-status` or `--name-only` for more informative output

Example: Finding when that folder was deleted in order to restore it
```bash
git log --all --name-status  -- 'src/test/scala/se/appland/somefolder*'
```
