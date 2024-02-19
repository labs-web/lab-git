---
layout: default
order: 2
---

# git diff


## How to show properly accents in git diff output

### Problème 
- [How to show properly accents in git diff output](https://stackoverflow.com/questions/29667339/how-to-show-properly-accents-in-git-diff-output)


When I run git diff command, in the files list all files with accents are poorly displayed :

 git diff --name-status xxxx yyyyyy
return

```
M       "\303\251\303\251.txt"
```

How I can preserve accents to have this ? :

```
M       "éé.txt"
```

### Solution

By default, git will print non-ASCII file names in quoted octal notation, i.e. "\nnn\nnn...".
This can be disabled with:


```bash
git config core.quotepath off   
# or
git config --global core.quotepath off

```


# Références
- []()