# Common Use Cases

## Modify commits

### Modify last commit of local branch

To change the commit message of the last commit use
```
git commit --amend -m 'New commit message'
```

To add some changes to the last commit
```
git add .
git commit --amend
```

___

## Switching branches 

### Switching branch with uncommitted changes

You can stage and commit the changes before switching branch
```
git commit -am 'Make some changes'
git switch anotherBranch
```

You can stash the changes before switching branch. Assuming you are on *main*...
```
git stash
git switch anotherBranch
```
Then, you can work on *anotherBranch*, come back to *main* and retreive the changes from the stash
```
git switch main
git stash pop
```
**Be careful** because this workflow doesn't work if you stash something else between the first `git stash` and `git stash pop`. In case you need to stash some other changes, you'd want to reference the stashes by stash index. See the notes or the docs for more details about stashing.

### Switching branches with untracked files

Normally, if you have untracked files and try to switch branch, those files are brought along with you without any notice. 
However, if the arrival branch has tracked files with the same name, this will generate a conflict.  
In this case, if you don't want to bring the file in the other branch, you can delete the file, add it to the index and commit, or stash it.
Then, you are free to switch branch.

If instead you need that file to override (or modify) the version in the other branch you can do the following:

If you don't need that file in the current branch but only in the other
```
git stash
git switch otherBranch
git stash pop
```
Here you'll have to resolve the conflict between the two versions of the file: the one already present in the branch and the one coming from the stash.  
When conflicts arise, the stash entry is not removed from the stash list. You have to drop it manually after resolving the conflicts
```
git stash drop
```

If you need the file also in the current branch
```
git commit -am 'Save the problematic file'
git switch otherBranch
git checkout firstBranch pathToThatFile/filename
```
Here you'll have to resolve the conflict between the two versions of the file: the one already present in the branch and the one coming from the checkout