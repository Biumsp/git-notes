# GIT Commits

GIT commits are like checkpoints. It is a snapshot of the repo at a particular state, along with a comment to describe what changed wrt the previous commit.  
There must be some changes wrt the previous commit, to be able to create a new one.  
Before committing we can select which changes to include in that commit. But pay attention to this: 
**You don't commit the changes. You commit the whole repo.**
But, since git operates at an higher level wrt the files, you can select to ignore the new version of a file when creating the new snapshot of the repo, by keeping the version from the previous commit.  
You select which changes to add to the commit by doing 
```
git add filename1 filename2 dirname
```
Or you can add all changes (i.e. include the new version of all changed files in the next commit). 
```
git add .
```
Where the dot is a wildcard character that means "all".

## Working directory, staging area & repository

The staging area is a non-physical place where added changes wait to be committed.

The *repository* is the .git folder. It is updated every time we make a commit.

`git add` stages the changes. `git commit` commits the changes (i.e. creates a new commit with some files updated, using the changes staged)

## Commits best practices

*Keep your commits atomic* (i.e. irreducible).  

The commit message should be shorted than 50 characters. Additional info can be given in the body of the commit message, but you should keep a blank line between the body and the header of the commit message. 

In the body keep the lines shorter than 72 characters.
Capitalize the first letter of the message header. Don't use the period at the end of the message header.

Focus on explaining what problem the commit solves. Why the canges were made rather then how (the code explains that).

# Commands & Options

```
git commit 
git commit -m 'Commit message here'
```

Modify last commit. You can change the message or include new changes in the commit. For the second option, you have to first stage them
```
git commit --amend
```

