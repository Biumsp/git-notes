# Installing GIT

## Windows bash installation

Windows machines do not come with a Unix-based prompt. They instead come with a different CLI (command line interface) called "command prompt".  
This causes an issue, because GIT needs to run on a Unix CLI.  
So we install the GIT bash, that gives us a Unix prompt and GIT along with it.  

In the [git download page](https://git-scm.com/downloads) click on the Windows option. Then install the right version for your pc.  
Leave all the default options, but you can change the default editor from Vim to whatever (like VSCode).  
Also, you should "override the default branch name for new repositories" and set it to "main", to make it coherent with Github.

Verify the installation with 
```
git --version
```

## GitKraken GUI

This is completely optional, but is very useful to visualize branches.  
Just download the installer from [here ](https://www.gitkraken.com/).  

Use present-tense imperative style.  
You should be able to read it like *"if I apply this commit it will.. commit message"*.