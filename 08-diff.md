# Git Diff

It is an informative command: it is used to show the difference between commits (local or remote).

Just *git diff* will compare the staging area and the working directory

## Git diff output analysis

The first line tells us which files are being compared

> diff --git a/filename b/filename

Typically it's the same file from two different versions, but you may also diff two sifferent files. *a* and *b* are the two versions.

The second line contains metadata about the file, like

> index 6255f..kcb762 100644

The next two lines tell us which identifier belongs to which file

> --- a/filename
> +++ b/filename

This means that the lines starting with a minus sign identify the changes in file *filename* from version *a*, while lines starting with a plus sign identify the changes in file *filename* from version *b*

The changes are shown after the "chunk header"

> @@ -x,y +z,k @@

Where instead of xyzk you will have numbers. There are informations about each individual file: -x,y indicates that in the file identified by the minus sign, y lines are shown, starting from line x. -z,k instead means that k lines of the other file are displayed, starting from line z.

Then, the lines that changed are displayed, preceded and followed by some "context" (the previous and next lines). Common lines are shown only once, without any identifier (+ or -).