# Git commands

## Change message of commit

`git commit --amend -m "New commit message"`

`git push --force` (only if it was pushed already)

## Undo commit

Undo commit and keep all files staged

`git reset --soft HEAD~`

Undo commit and unstage all files

`git reset HEAD~`

Undo the commit and completely remove all changes

`git reset --hard HEAD~`

## Delete merged branches

Merged into **master**

`git branch --merged master | grep -v "\* master" | xargs -n 1 git branch -d`

## Delete Branch Local and Remote

```bash
$ git push -d <remote_name> <branchname>  // Remote
$ git branch -d <branchname> // Local
```

**Note:** In most cases, `<remote_name>` will be `origin`

## Rename local and remote branch

```
# Rename the local branch to the new name
git branch -m <old_name> <new_name>

# Delete the old branch on remote - where <remote> is, for example, origin
git push <remote> --delete <old_name>

# Push the new branch to remote
git push <remote> <new_name>

# Reset the upstream branch for the new_name local branch
git push <remote> -u <new_name>
```

## Pull and overwrite everything local

`git fetch --all`

`git reset --hard origin/branch-name`

## Cherry pick changes to merge to master

Go to master and pull latest

```bash
git checkout master
git pull
```

Find sha of commit we want to cherry pick, eg: `mylongshacommit`

Create new branch from master, eg: `fix-with-my-cherry-pick`

On the new created branch, do cherry pick of commit

```bash
git cherry-pick mylongshacommit
```

If any conflict, solve it and continue with `git cherry-pick --continue`

Push branch `fix-with-my-cherry-pick` and create PR to merge to master

## Revert one file

```bash
git checkout commitHash~amountOfCommitsYouWantToGoBack path/of/file

example: this reverts the file to the version immediate before from that commit
git checkout asdH8SA~1 path/of/file
```

## Create an empty commit (eg: trigger a process)

```bash
git commit --allow-empty -m "trigger pipeline"
```
