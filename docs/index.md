## Table of contents

- [Configuration](#configuration)
- [Branches](#branches)
- [Staging and committing](#staging-and-committing)
- [Undoing things](#undoing-things)
- [History](#history)
- [Stash](#stash)
- [VI](#vi)

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

[Go to top](#table-of-contents)

## Branches

### Checkout

```bash
# create a new branch
git checkout -b branch_name
```

### Rename

```bash
git branch -m <newname>
```

### Delete

```bash
# search for "branch_name" in all branches
git branch -a | grep branch_name

# delete local branch
git branch -d local_branch_name

# delete remote branch
git push origin -d remote_branch_name

# delete branches which no longer exist on the remote
git fetch -p
```

### Push

```bash
# safer alternative of force push
git push --force-with-lease
```

[Go to top](#table-of-contents)

## Staging and committing

```bash
# staging patches
git add --patch foo.txt
```

[Go to top](#table-of-contents)

## Undoing things

### Revert

```bash
# Creates a new commit which reverts the changes of 2b504be
git revert 2b504be
```

### Reset

```bash
git reset
git reset --hard
git reset --soft HEAD~1

# Reset branch to the state of remote master
git fetch origin
git reset --hard origin/master
```

### Amend

```bash
# Modify the author of the last commit, keep the message untouched
git commit --amend --no-edit --author="John Doe <john@example.org>"

# Add a left out file to the last commit
git add some/changed/file.ext
git commit --amend -m "commit message"
```

[Go to top](#table-of-contents)

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

[Go to top](#table-of-contents)

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

### "Remote stash"

Save the incomplete work to the remote server on your branch.

```bash
# Nothing special, save the current state to the remote
git add .
git commit -m "wip"
git push

# Revert the last commit, continue the work 
git reset --soft HEAD^

# Commit the completed work
git add .
git commit -m "added a cool feature"

# Be careful! This command will rewrite the history of the remote branch.
git push --force-with-lease
```

[Go to top](#table-of-contents)

## VI

### Quit

Commands | Description
--- | ---
Press <kbd>Esc</kbd>, type `:q`, press <kbd>Enter</kbd> | Quit
Press <kbd>Esc</kbd>, type `:q!`, <kbd>Enter</kbd> | Quit without saving
Press <kbd>Esc</kbd>, type `:wq`, press <kbd>Enter</kbd> | Save and quit

### Switch between modes

Commands | Description
--- | ---
Press <kbd>Esc</kbd> | Command mode
Press <kbd>Esc</kbd>, type `i` | Switch to insert mode
Press <kbd>Esc</kbd>, type `R` | Switch to replace mode

### Editing

Commands | Description
--- | ---
Press <kbd>Esc</kbd>, type `o` | Insert a blank line below the current line
Press <kbd>Esc</kbd>, type `O` | Insert a blank line above the current line

[Go to top](#table-of-contents)
