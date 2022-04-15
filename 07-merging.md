# Merging Branches

We merge branches. Not commits.
We merge branches to incorporate the work done on a branch, into another.  

## Fast Forward vs. Non Fast Forward 

If branch B is a direct descendant of the commit branch A points to, we can merge B into A with a fast forward merge: the merge only introduces changes, and no conflicts can arise. 
In git, these changes are automatic.  
If instead branch A has new commits after the one branched B branched from, the merge is not a fast forward merge.  

Basically, it is a fast forward merge when branch A points to a commit in branch B history.

## Fast Forward merges

When performing a fast forward merge
```
git switch main
git merge other
```
The first command makes HEAD point to *main*.
The second command moves the pointer of branch *main* to the same commit *other* points to.  
Now the *main* branch contains all the commit history of *other*.


## Non Fast Forward merges

Non fast forward merges behave differently. Since the branch we merge into has some commits the other branch has not, there can be conflicts. Conflicts arise whenever the top commits of the two branches show differences in the same lines of the same files. 

Non fast forward merges generate a *merge commit*. This commit is a snapshot of the working tree right after the merge. It is a case of a commit with two parent commits.  

If there are no conflicts, you just select a commit message for the merge commit. Git will merge the changes automatically.  

If there are conflicting changes we have to manually resolve them. The files with conflicts are changed: conflict markers are added to highlight which lines are conflicting. The markers tell us how those lines appear in the current HEAD branch, and in the branch we are trying to merge in.  
It is up to you to choose which lines to keep (and we remove the markers).