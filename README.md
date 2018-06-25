
1. save username and password 

```
git config credential.helper store
```

2. undo the first commit ( assuming there is only one commit in the history)

```
git update-ref -d HEAD
```
3. undo the last (n) commits and return the changed files to staging area

```
git reset --soft HEAD~n
``` 
4. print the number of commits on all branches grouped by authors

```
git shortlog -s -n --all
```
5. undo a pushed commit in the remote repository, on master branch

```
git push origin +{commit-id}^:master
```
6. See all the upstream repository urls

```
git remote -v
```

7. change the author date when committing changes
```
git commit --date "date-format" -m "commit message"
```

8. Show the list of branches
```
git show-branch
```

9. Show the list of tags on the current branch
```
git tag
```
10. Show all the configurations for the current repository

```
git config -l
```

11. remove a file from the staging area

```
git reset <file_name>
```

12. remove all files of a folder from the staging area
```
git reset <folder_name>/
```
13. see the changes in the files added to the staging area
```
git diff --staged
```
14. change the url of remote repository
```
git remote set-url <remote_name> <url>
```

15. ignore changes to already tracked files
```
git update-index --assume-unchanged <file>
```

another alternative :
```
git update-index --skip-worktree <file> 
```
[ more information on difference between assume-unchanged and skip-worktree.](https://stackoverflow.com/a/13631525/2450855)

16. ignore changes to already tracked files in a folder
```
git update-index --assume-unchanged <folder_name>/
```
17. undo tip 15 & 16 : start tracking files again

```
git update-index --no-assume-unchanged [<file> ...]
```
18. show list of tags, sorted by date descendingly
```
git tag --sort=-creatordate
```
19. delete tag from the local repository
```
git tag --delete tagname
```
20. delete tag from the remote repository
```
git push --delete origin tagname 
```
21. clone all branches in a remote repository

First, clone the remote repository :
```
git clone "remote repository url"
```
Then, see what branches exist in this repository
```
git branch -a
```

If you just want to take a quick peek at an upstream branch :
```
git checkout origing/branch_name
```
Finally, if you want to continue developing on that branch, you should
```
git checkout -b branch_name
```
22. see which commit a tag points to
```
git rev-parse tagname
```
