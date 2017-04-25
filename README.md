
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
4. see the number of commits on all branches by all authors

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