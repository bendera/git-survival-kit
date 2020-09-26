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

### Reverting commits

`git revert 2b504be` revert a commit<br>
`git commit --amend -m "This is the correct message"`<br>
```
git add some/changed/file.ext
git commit --amend -m "commit message"
```

### Editing author in multiple commits

```shell
# bash comment example
git filter-branch --env-filter '
WRONG_EMAIL="wrong@example.com"
NEW_NAME="New Name Value"
NEW_EMAIL="correct@example.com"

if [ "$GIT_COMMITTER_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$WRONG_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

## History

```
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