# Git Commands

* `git add .` or `git add --all` - To add/Stage files.
* `git commit -m "<Your message>"` - To commit with your message.
* `git push origin <branch-name>` - To push to the branch of yours. (If you are gonna push it to the `master` then you don't have to mention the branch name.)
* `git diff 51473e57 cfbf054b` - To see the diff between 2 commit hashes.
* `git status` - To check the status of files in the working directory (staged, unstaged, untracked).
* `git log` - To view the commit history of the current branch.
* `git log --oneline` - To view a simplified version of the commit history (one commit per line).
* `git branch` - To list all local branches.
* `git branch <branch-name>` - To create a new branch.
* `git checkout <branch-name>` - To switch to a different branch.
* `git checkout -b <branch-name>` - To create and switch to a new branch in one command.
* `git merge <branch-name>` - To merge the changes from another branch into the current branch.
* `git pull origin <branch-name>` - To fetch and merge changes from the remote repository into your local branch.
* `git clone <repository-url>` - To clone a remote repository to your local machine.
* `git remote -v` - To list the remote repositories associated with your local repository.
* `git reset <file-name>` - To unstage a file that has been added using `git add`.
* `git reset --hard` - To reset your working directory to match the latest commit (warning: this will discard changes).
* `git fetch` - To fetch changes from the remote repository without merging them.
* `git stash` - To temporarily save changes that you don't want to commit yet.
* `git stash pop` - To apply the most recent stashed changes.
