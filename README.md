
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
git checkout origin/branch_name
```
Finally, if you want to continue developing on that branch, you should
```
git checkout -b branch_name
```
22. see which commit a tag points to
```
git rev-parse tagname
```
23. revert branch history to a specific tag, discarding all changes after the tag
```
git reset --hard tagname
```

24. revert branch history to a specific tag, keeping all changes after the tag in the staging area
```
git reset --soft tagname
```
25. Show both the `AUTHOR_DATE` and `COMMITTER_DATE` of commits 
```
git log --format=fuller
``` 
26. ##### The difference between `GIT_AUTHOR_DATE` and `GIT_COMMITTER_DATE` :

There are two kinds of timestamp in git: a `GIT_AUTHOR_DATE` and a `GIT_COMMITTER_DATE`. Although in most cases they both store the same value, they serve slightly different purposes. As the documentation depicts :   
```
The author is the person who originally wrote the work, whereas the committer is the person who last applied the work.
```
So if, for instance, you send in a patch to a project, the author date will be when you made the original commit but the committer date will be when the patch was applied. Another common scenario is rebasing: rebasing will alter the commit date, but not the author date.

27. changing the `AUTHOR_DATE` and `COMMITTER_DATE` of a commit in git
```
$ export GIT_AUTHOR_DATE="Wed Feb 16 14:00 2037 +0100"
$ export GIT_COMMITTER_DATE="Wed Feb 16 14:00 2037 +0100"
$ git commit ...
```
28. filtering history of commits in date ranges using `since` and `until` options

```
git log --since='yesterday'
```
```
git log --since="1 week ago" --until="yesterday"
```
29. showing commit history with summary of changes made in each commit
```
git whatchanged 
```
also, the `since` and `until` options can be used to filter history
```
git whatchanged --since='2 weeks ago' --until=`2 days ago`
```
30. delete local and remote branches

to remove local branch 
```
git branch -D branch_name
```
to remove a remote branch

```
git push --delete remote_name branch_name
```
31. see the changes to a file in a commit
```
git show commit_hash -- file_name
```