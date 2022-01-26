# branch

### List branch

```
# See both local and remote branches
git branch -a 

# See only remote branches
git branch -r

```

### Checkout

```
git checkout branchName

# Checkout a remote branch and rename it 
git checkout -b RenameBranch <name of remote>/BranchName

```

### Delete

```
# https://www.cloudbees.com/blog/git-delete-branch-how-to-for-both-local-and-remote

1) delete local branch
git branch -d <branch-name>

2) force delete local branch
git branch -D <branch-name>

3) delete remote branch
git push --delete <remote name> <branch name>

```

### Pull all remote branches

```
git branch -r 
git fetch --all
git pull --all

git branch -a

```
