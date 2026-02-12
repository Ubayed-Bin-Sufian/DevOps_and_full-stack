# Git Commands (Lab)

## Install Git manual pages

```bash
sudo apt-get install git-man
```

### how to use it?

```bash
man git-<command>
```

## List of Git commands

`git rm --cached <file>`: This command removes the specified file from the staging area (index) but keeps it in the working directory. It is used when you want to unstage a file that has been added to the staging area.
`echo notes.txt >> .gitignore`: This command appends the filename "notes.txt" to the .gitignore file. The .gitignore file is used to specify files or directories that should be ignored by Git when tracking changes. By adding "notes.txt" to the .gitignore file, you are telling Git to ignore any changes made to that file in future commits.