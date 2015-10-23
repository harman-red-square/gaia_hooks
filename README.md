# hooks
This repo contains hooks which can be usefull for Internal Harman development process.
1. Commit message checker (commit-msg)
2. Adding temp patch (pre-commit,post-commit)
3. Removing temp patch 

**How to use git hooks for Gaia**

1. Clone hooks repo to your local gaia git hooks folder.
from B2G/gaia folder
```
cd .git/hooks
git init
git remote add origin https://github.com/harman-red-square/hooks.git
git pull origin master
cd ../..
```
2. Apply patch on clean branch (Bug 1142855 - Implement softkey feature on the simple phone from https://github.com/harman-red-square/gaia/pull/5)
```
.git/hooks/post-commit
```
3. For each commit you do in gaia repo 'git hooks' will remove patch before commit and apply patch again after commit.
So files changed in patch will not be added into your commit.
Please pay attention!

**How to remove git hooks for Gaia**
```
cd .git/hooks
git ls-files | xargs rm -f
rm -rf functions
rm -rf .git
cd ../..
```
