# Welcome to my Linux Commands Page

# GIT
#### Reset a Branch to another Branch
```
git checkout mybranch
git reset --hard mainbranch
```
#### Cherrypick a commit from a different branch
```
git cherrypick <commitid>
```
#### Delete a branch from remote
```
git push -d <branch name>
```
#### Create a Patch from last commited change
```
git diff HEAD~ > <somefile>.diff
```
#### Apply a Patch from diff
```
git apply < <somefile>.diff
```
# Linux
#### List of open files by a process
```
lsof -p <pid>
```
# Docker
#### Delete all docker images from the system
```
docker rmi -f `docker images -aq`
```
