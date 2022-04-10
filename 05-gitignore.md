# .gitignore file

There are files you don't wanna track. Like:  
- Files generated by text editors
- Credentials, private data
- Log files

For that we use a *.gitignore* file, usually in the root of the repository.  
This file can contain file names, folder names or pattern.  
The * character matches every character but /.

The ? character matches one single character. The non-greedy version of *


## Examples

```
*.dep           # Ignores all files with .dep extention

lnInclude/      # Ignores the folder lnInclude

folder1/*.C     # Ignores every C file in folder1

**/*~           # Ignores every file ending with ~ in every subdirectory 
```

## Refresh after changing .gitignore

If you already staged some changes and then update the .gitignore file, the new ignore patterns won't have any effect on the staged files. You have to remove them from the index and add them again. This because the gitignore patterns have an effect only when staging files.

```
git rm -r --cached .
git add .
```

Now the staged file will be coherent with the gitignore file.  
**BE CAREFUL** with `git rm` because it removes files from the working tree and the staging area. The option *--cached* is needed to preserve the files in the working tree.