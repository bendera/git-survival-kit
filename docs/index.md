## Configuration

### Configure name and email

```bash
git config [--global] user.name "John Doe"
git config [--global] user.email "jdoe@example.org"
```

### Configure aliases

```bash
git config [--global] alias.foo checkout
git config [--global] alias.bar "reset HEAD --"
```

### Set Visual Studio Code as default editor

```bash
git config [--global] core.editor "code --wait"
# or
git config [--global] core.editor "C:\Users\<username>\AppData\Local\Programs\Microsoft VS Code\Code.exe --wait"
```

### Ignore files locally

Edit ```.git/info/exclude```<br>

## Branches

```bash
# create a new branch
git checkout -b branch_name

# search for "branch_name" in all branches
git branch -a | grep branch_name

# delete local branch
git branch -d local_branch_name

# delete remote branch
git push origin -d remote_branch_name

# delete branches which no longer exist on the remote
git fetch -p

# safer alternative of force push
git push --force-with-lease
```

## Staging and committing

```bash
# staging patches
git add --patch foo.txt

# Modify the author of the last commit
git commit --amend --no-edit --author="John Doe <john@example.org>"
```

## Undoing things

```bash
# Creates a new commit which reverts the changes of 2b504be
git revert 2b504be

git reset
git reset --hard
git reset --soft HEAD~1

git add some/changed/file.ext
git commit --amend -m "commit message"
```

## History

```bash
# Search in commit messages
git log --grep="foo"

# Example result:
# * 3823c9b 2020-09-26 | Initial commit [John Doe]
git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short

# More examples
git log --pretty=oneline --max-count=2
git log --pretty=oneline --since="5 minutes ago"
git log --pretty=oneline --until="5 minutes ago"
git log --pretty=oneline --author="John Doe"
git log --pretty=oneline --all
```

## Comparing branches and revisions

## Submodules

## Stash

```bash
# stash with message, include untracked
git stash push -u -m "Foo bar"

# list stashed changes
git stash list

# Apply stash
git stash apply
git stash apply "stash@{2}"
# Git 2.11 and above:
git stash apply 2

git stash pop

git stash drop

git stash clear
```
