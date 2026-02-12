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
`git log --name-only`: This command displays the commit history along with the names of the files that were changed in each commit. It shows the commit hashes, commit messages and the corresponding file names, allowing you to see which files were modified in each commit.
`git log --oneline`: This command displays the commit history in a condensed format, showing only the commit hashes and the first line of the commit messages. It provides a quick overview of the commit history without displaying the full commit messages or file changes.
`git log --max-count=3`: This command limits the number of commits displayed in the log to a maximum of 3. It shows only the most recent 3 commits in the commit history, allowing you to focus on the latest changes without overwhelming you with the entire commit history.