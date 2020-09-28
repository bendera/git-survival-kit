## Configuration

```bash
# Configure name and email
git config [--global] user.name "John Doe"
git config [--global] user.email "jdoe@example.org"

# Configure aliases
git config [--global] alias.foo checkout
git config [--global] alias.bar "reset HEAD --"

# Set Visual Studio Code as default editor
git config [--global] core.editor "code --wait"
```

### Ignore files locally

Edit ```.git/info/exclude```<br>

## Branches

```bash
# delete local branch
git branch -d local_branch_name

# delete remote branch
git push origin -d remote_branch_name

# delete branches which no longer exist on the remote
git fetch -p
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

git reset --hard
git reset
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

`git stash list`<br>
`git stash push -u -m "Foo bar"` stash with message, include untracked