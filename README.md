# hooks
This repo contains hooks which can be usefull for Internal Harman development process.

1. Commit message checker (commit-msg)

2. Adding temp patch (post-commit)

3. Removing temp patch (pre-commit)


**How to use git hooks for Gaia**

1) Clone hooks repo to your local gaia git hooks folder.

from B2G/gaia folder
```
cd .git/hooks
git init
git remote add origin https://github.com/harman-red-square/hooks.git
rm -f pre-commit
git pull origin master
cd ../..
```

#"rm -f pre-commit" this is temp 

2) Apply patch on clean branch (Bug 1142855 - Implement softkey feature on the simple phone from https://github.com/harman-red-square/gaia/pull/5)
```
.git/hooks/post-commit
```

3) For each commit you are doing 'git hooks' will remove patch before commit and apply patch again after commit.
So files changed in patch will not be added into your commit.
Please pay attention!

**How to turn ON/OFF git hooks by Git Config**

Turn ON/OFF 'commit message checker' hook
```
git config --local hooks.allow-commit-msg-check true
git config --local hooks.allow-commit-msg-check false
```
Turn ON/OFF 'adding temp patch' hook

```
git config --local hooks.allow-patch true
git config --local hooks.allow-patch false
```

**How to remove git hooks for Gaia**

from B2G/gaia folder
```
cd .git/hooks
git ls-files | xargs rm -f
rm -rf functions
rm -rf .git
cd ../..
```
