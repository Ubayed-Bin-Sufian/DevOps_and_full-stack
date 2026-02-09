# Git commands

`git init` (Initialize a new Git repository) <br>
`git status` (Check the status of the repository) <br>
`git add <file>` (Stage changes for the next commit) <br>
`git add .` (Stage all changes for the next commit) <br>
`git commit -m "message"` (Commit staged changes with a message) <br>
`git commit -am "message"` (Stage and commit changes in one step) <br>
`git restore --staged <file>` (Unstage a file) <br>
`git log` (View commit history) <br>
`git log --oneline` (View commit history in a condensed format) <br>
`git reset <commit>` (Reset to a specific commit; NOTE: each commit is built on top of each other. We cannot remove a commit from the middle.) <br>
`git reset --hard <commit>` (Reset to a specific commit and discard all changes) <br>
`git stash` (Temporarily save changes that are not ready to be committed) <br>
`git stash pop` (Reapply stashed changes) <br>
`git stash clear` (Clear all stashed changes) <br>
`git remote add origin <repository_url>` (Add a remote repository) <br>
`git remote -v` (View remote repositories) <br>
`git push origin main` (Push changes to the remote repository on the main branch) <br>
`git branch <branch_name>` (Create a new branch) <br>
`git switch <branch_name>` (Switch to a different branch) <br>
`git merge <branch_name>` (Merge a branch into the current branch) <br>
`git remote add upstream <original_repository_url>` (Add the original repository as a remote) <br>
`git push origin <branch_name> -f` (Force push changes to a branch) <br>

### To update the fork with the upstream

1. In forked repo, click Sync fork --> update branch (updates the main branch) --> from git, swtich to the target branch, then `git merge main` and resolve conflicts if any. 

OR

2.  checkout to main branch: `git switch main` <br>
    fetch upstream changes: `git fetch --all --prune` <br>
    reset the main branch of origin to the upstream: `git reset --hard upstream/main` <br>
    now the local system has all the changes from upstream <br>
    push the changes to your forked repo: `git push origin main --force`

OR

3. `git pull upstream main` (pull changes from the upstream main branch to your local main branch) <br>
   `git push origin main` (push the updated main branch to your forked repository) <br>

### Merge commits to a single commit

1. `git log` (Identify the commit hash of the commits you want to merge) <br>
2. `git rebase -i <commit_hash>^` (Start an interactive rebase from the commit before the first commit you want to merge) <br>
3. In the interactive rebase editor, change the word "pick" to "squash" (or "s") for the commits you want to merge, leaving "pick" for the first commit. <br>
4. Save and close the editor. Git will then combine the commits into a single commit. <br>
5. If prompted, edit the commit message for the new combined commit, then save and close the editor. <br>
6. Finally, push the changes to the remote repository using `git push origin <branch_name> --force` (force push the changes to update the remote branch with the new commit history). <br>

## Glossary

- **HEAD**: A reference to the latest commit in the current branch. <br>
- **Commit**: A snapshot of changes in the repository. <br>
- **fork**: A personal copy of someone else's repository. <br>
- **upstream**: The original repository from which a fork was created. <br>