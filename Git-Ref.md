## Git commands
- git init – creates and initializes a directory on your local machine
```
    git init <path/folder-name-goes-here>
```

- git add – adds a file to the staging area to be committed
```
    git add <fileName.txt>
```

- git commit – commits the file for tracking and version control.  The -m allows message on command line
```
	git commit -m ‘meaningful message for commit goes here’
```

- git log –oneline –decorate –graph -all – command shows commits, graph, and visual of branches

- git remote -v – command shows verbose display of the URL for the push to github

- git push -u origin master – commits changes to github repo
	When you clone a repo, Git automatically creates a remote named origin that references the clone URL
	master refers to your local repo where you have done your commits

- git clone <URL> - command lets you create a copy of a repo from github on your local machine

- git remote set-url origin <https://github.com/thesoftwareguild/helloworld.git> - command lets you change or set the remote URL repo link.

- git branch – command shows all branches


## Instructions to push code to new repo
1. Initialize Git (if not already done):
```
git init
```
This command initializes a new Git repository in your current directory. It creates a .git directory that tracks all changes to your files.


2. Add your files to the staging area:
```
git add . 
//or 
git add --all
```
The git add . command stages all the changes in your current directory (and subdirectories) for the next commit. The . signifies all files and directories.


3. Commit your changes:
```
git commit -m "Initial commit"
```
This command creates a snapshot of your staged changes. The -m flag allows you to add a commit message, which in this case is “Initial commit”. This message helps you and others understand what changes were made in this commit.

4. Add the remote repository:
```
git remote add origin https://github.com/your-github-username/your-repo.git
```
This command links your local repository to a remote repository on GitHub. origin is the default name given to this remote repository, and the URL is the location of your GitHub repository.


5. Push your code to the main branch
```
git push -u origin main
```
This command uploads your local commits to the remote repository. The -u flag sets the upstream branch, meaning future git push commands will default to pushing to origin main.

## Notes on Git
*** rm -rf .git    
- This command removes the .git directory from the current folder.  This command will effectively remove the folder from git.  You will lose any changes or tracking done previously.   Be careful when using this command.  In Windows you can also delete the .git hidden folder using Explorer.
  
*** You should be in a clean state when branching.