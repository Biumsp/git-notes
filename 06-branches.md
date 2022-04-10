# GIT branches

Git branches are a way to separate changes on the base of their context.  

We are always on a branch. When we `git init` the default branch is created. It has nothing special. It's just a branch like the others. But often special attentions are given to it by the users. 

Using `git branch newBranch` creates a new branch **based upon the current HEAD**


## HEAD

HEAD is a pointer, that points to the current location in the repository. It points to the branch we are *checking out*.  
The branch itself is a pointer, that points to the last commit.. of that branch, the tip of the branch.  
HEAD is a reference to a branch pointer. And the branch pointer is a reference to the most recent commit of the branch.

HEAD is what determines to which branch new commits are assigned. If HEAD -> main, new commits will extend the "main"s branch. If HEAD -> feature, new commits will extend the "feature" branch.

It also determines what we see in the working directory (the working tree).  

When we create a new branch, if we git log, we get something like this:  
> commit kdhfg687c8wedh8a9he8z8n7yedbd782 (HEAD -> main, newBranch)  
> Author: username \<email@gmail.com>  
> Date:   Tue Jan 26 18:23:03 2022 +0100  
>
>    Make fake commit  

This means that we have two branches, main and newBranch, pointing to the same commit. And we are checking out main, because HEAD -> main

We can point HEAD to newBranch in two ways
```
git switch newBranch        # new way
git checkout newBranch      # old way
```

Now, if we git log we see:  

> commit kdhfg687c8wedh8a9he8z8n7yedbd782 (main, HEAD -> newBranch)  
> Author: username \<email@gmail.com>  
> Date:   Tue Jan 26 18:23:03 2022 +0100  
>
>    Make fake commit  

And if we make some changes, stage and commit them..  

> commit lsklcnon47rhf920dj1nddksdnq9d9nx (HEAD -> newBranch)  
> Author: username \<email@gmail.com>  
> Date:   Tue Jan 26 18:29:14 2022 +0100  
>
>    New fake commit on newBranch 
>
> commit kdhfg687c8wedh8a9he8z8n7yedbd782 (main)  
> Author: username \<email@gmail.com>  
> Date:   Tue Jan 26 18:23:03 2022 +0100  
>
>    Make fake commit 

Main is still at the previous commit, but newBranch now points to a new commit: its tip extended. And HEAD still points to newBranch.  
If we `git switch main`  

> commit kdhfg687c8wedh8a9he8z8n7yedbd782 (HEAD -> main)  
> Author: username \<email@gmail.com>  
> Date:   Tue Jan 26 18:23:03 2022 +0100  
>
>    Make fake commit 

We don't see the last commit because it is not in the main branch history. The tip of main points to a previous commit. That commit exists only in newBranch.


# Commands & Options

Get a list of local branches, with an * for the branch we are currently checking out (the one HEAD points to)
```
git branch     
```

Create a new branch that points to where HEAD points. 
```
git branch newBranchName
```
We get a branch whose tip is whatever commit we were checking out with HEAD. It can be the last commit of a branch (in that case, we are checking out a branch) or an intermediate commit (in that case, we are in detached head state).  

Switch to another branch
```
git switch branchName
```

The old way to switch branches was 
```
git checkout branchName
```
But switch is now preferred, because *checkout* does a lot of other stuff too, while *switch* is only for switching (with all the possible options").  

Create a branch and switch to it (same command with switch and checkout)
```
git switch -c newBranch
git checkout -b newBranch
```  

Delete a branch. First be sure you are on another branch
```
git branch -d branchName
```
This works only if the branch is fully merged into its upstream. If you want to delete the branch anyway
```
git branch -d -f branchName
```
Or the shortcut
```
git branch -D branchName
```
**be careful when using --force**

To rename a branch, switch to the branch you want to rename
```
git switch oldNameOfBranch
git branch -m newNameOfBranch
```

# Behind The Scenes

How does git manage HEAD and branches?  
In the *.git* folder there is a file named HEAD. That file contains a string like this

> ref: refs/heads/main

This is just a pointer to the *main* branch file.  
In the *.git/refs/heads/* directory there is a file for every branch. These files contain the commit hash of their last commit.  

So, when committing, we change the file of the branch we are currently on. When switching, we change the HEAD file. When we create a new branch, we create a file in the *.git/refs/heads/* directory.

When we are in detached-head state, the file *.git/HEAD* contains the commit hash of the commit we are checking out, like

> 277dae51fcd89a45a352903f50a9dad7ab2fc5c8






