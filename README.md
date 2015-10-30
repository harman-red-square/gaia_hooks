# hooks
This repo contains hooks which can be usefull for Internal Harman development process.

1. Commit message checker (commit-msg)

2. Adding/removing temp gaia patch (post-commit,pre-commit)

3. Post commit coding style check (git_diff_to_lint.sh)

**How to install git hooks for Gaia**

Clone hooks repo to your local gaia git hooks folder.

from B2G/gaia folder
```
cd .git/hooks
git init
git remote add origin https://github.com/harman-red-square/hooks.git
rm -f pre-commit
git pull origin master
cd ../..
```
Note, that "rm -f pre-commit" is temp

**How to use git hooks for Gaia**

1) Commit message checker (commit-msg)
*  Commit Message Checker help to follow the template and reject commits which doesn't follow the template.
http://stteamsite.symphonyteleca.com/redsquare/Wiki/Commit_message_template.aspx


* Turn ON/OFF 'commit message checker' hook
```
git config --local hooks.allow-commit-msg-check true
git config --local hooks.allow-commit-msg-check false
```

2) Adding/removing temp gaia patch (post-commit,pre-commit)

* Apply patch on clean branch (Bug 1142855 - Implement softkey feature on the simple phone from https://github.com/harman-red-square/gaia/pull/5)

```
.git/hooks/post-commit
```

* For each commit you are doing 'git hooks' will remove patch before commit and apply patch again after commit.
So files changed in patch will not be added into your commit.
Please pay attention!

* Turn ON/OFF 'adding temp patch' hook

```
git config --local hooks.allow-patch true
git config --local hooks.allow-patch false
```

3) Post commit coding style check (git_diff_to_lint.sh)

Script "git_diff_to_lint.sh" helps to check changes made by existing commit by Lint.

Usage:
    
```
.git/hooks/git_diff_to_lint.sh <baseline> <commit for check>​
```

**How to remove git hooks from repo**

from B2G/gaia folder
```
cd .git/hooks
git ls-files | xargs rm -f
rm -rf functions
rm -rf .git
cd ../..
```
