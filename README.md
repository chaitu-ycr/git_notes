# git_notes

## git configuration 👇
- Git configuration allows you to personalize how Git works for you. It's like setting preferences for any other software.
- There's a command called `git config` that lets you set and view these settings.
- check your current configuration ➡️ `git config --list`
- configure email and name globally
    - email id ➡️ `git config --global user.email "enter email id"`
    - user name ➡️ `git config --global user.name "enter your name"`
- add notepad++ as a global text editor ➡️ `git config --global core.editor notepad++`

## ssh key generation 👇
- generating SSH keys is a crucial step for using Git over SSH to securely connect to remote repositories like GitHub or GitLab.
- `ssh-keygen -t rsa -C "enter email id"`
    - `ssh-keygen` This is the command to generate the SSH key pair.
    - `-t ed25519` This specifies the key type. Ed25519 is a modern and secure option. You can use `-t rsa -b 4096` for RSA keys if your Git provider requires it, but Ed25519 is generally preferred.
    - `-C "your_email@example.com"` This adds a comment to your key with your email address. This is helpful for identification.
- command will generate two keys
    - A private key (usually named `id_rsa`) - This key should be kept confidential and never shared.
    - A public key (usually named `id_rsa.pub`) - You'll need to add this public key to your Git provider account.

## clone repository 👇
- `git clone` command is your gateway to creating a local copy, or clone, of a remote Git repository.
    - basic syntax ➡️ `git clone [url] [directory_name]`
    - `git clone https://github.com/chaitu-ycr/git_notes.git`
- other options
    - clone to a specific path
        - `git clone https://github.com/chaitu-ycr/git_notes.git <user_defined_repo_path>`
    - Clone a specific branch
        - use the `-b` flag to specify a particular branch to clone instead of the default branch.
        - `git clone -b <branch_name> https://github.com/chaitu-ycr/git_notes.git <user_defined_repo_path>`
    - Clone with mirror.
        - `--mirror` flag creates a local copy that reflects all branches and tags from the remote repository. This is useful for making a complete backup.
        - `git clone --mirror https://github.com/chaitu-ycr/git_notes.git`
    - Sparse clone
        - `--sparse` flag creates a lightweight clone that downloads only the minimum information needed to checkout a specific commit. This can save disk space.
        - `git clone --sparse https://github.com/chaitu-ycr/git_notes.git`

## git checkout 👇
- `git checkout` command is a versatile tool in Git with several functionalities
- Switching Branches
    - switch between different branches in your local repository
    - `git checkout <branch_name>`
- Detaching the HEAD
    - use the `-d` flag to detach the HEAD
    - `git checkout -d <branch_name>`
- Creating a New Branch ➡️ `git checkout -b <new_branch_name>`
- Restoring a File ➡️ `git checkout <commit_hash> <file_path>`
- Checkout with Checkout Index
    - Checkout all staged files ➡️ `git checkout`
    - Checkout a specific staged file ➡️ `git checkout <file_path>`

## git branch 👇
- Listing Branches ➡️ `git branch`
    - show all remote tracking branches ➡️ `git branch –a`
    - list the branches with additional information ➡️ `git branch –v`
    - only show merged branches ➡️ `git branch –m`
- Creating a New Branch ➡️ `git checkout -b <new_branch_name>`
- Deleting a Branch ➡️ `git branch -d <branch_name>`
- Renaming a Branch ➡️ `git branch -m <old_branch_name> <new_branch_name>`
- Merging Branches ➡️ `git merge <branch_name>`

## git fetch 👇
- `git fetch` ➡️ downloads updates from a remote repository without merging them into your local working directory.
- command is essential for staying up-to-date in Git workflows.
- `git fetch <remote> <branchname>`
- Basic Fetch ➡️ `git fetch origin`
- Fetching Specific Branch ➡️ `git fetch origin main`
- Pruning Stale Tracking Branches ➡️ `git fetch --prune origin`
- Fetches from all configured remotes ➡️ `git fetch --all`
- Fetches only tags ➡️ `git fetch --tags`
- Limits the fetch to a specific number of commits ➡️ `git fetch --depth=<number>`
- Shows what would be fetched without making any changes ➡️ `git fetch --dry-run`

## git pull 👇
- `git pull` command is a convenient shortcut that combines the functionality of `git fetch` and `git merge` in a single step.
- `git pull [<remote>] [<branchname>]`
- Basic Usage ➡️ `git pull origin`
- Specifying Branch ➡️ `git pull origin main`    - 
- It's generally a good practice to run `git fetch` first to see what changes are available before using `git pull` to avoid unintended merges.
- More Options
    - `--rebase` ➡️ Rebases your local commits on top of the remote branch instead of creating a merge commit. This can lead to a cleaner commit history but can be risky if you've already shared your local branch.
    - `--force` ➡️ Forces the merge even if there are local uncommitted changes. This can be dangerous and should be used with caution.
    - `--all` ➡️ Fetches from all configured remotes.

## git add 👇
- `git add` command is your gateway to including changes in your Git repository. It instructs Git to prepare specific files or directories for the next commit.
- Basic Usage ➡️ `git add <filename>`
- Adding Multiple Files
    - Explicit Listing ➡️ `git add file1.txt file2.txt file3.js`
    - Using Wildcards ➡️ `git add *.txt`
- Adding All Staged Changes ➡️ `git add .`
- Adding All Changes (Staged and Unstaged) ➡️ `git add -A`
- More Options
    - `-f` ➡️ Forces adding files even if they are ignored by Git. Use with caution as it bypasses exclusion rules.
    - `-p` ➡️ Patches the content of a file interactively, allowing line-by-line staging of changes.
    - `-u` ➡️ Updates the index with only the latest changes in a file, effectively refreshing the staged content.
- create or add new files ➡️ `git add <new filename>`

## git status 👇
- `git status` command is your window into the current state of your Git repository. It provides a clear picture of what's happening with your files, helping you understand which changes are tracked, staged, and untracked.
- Basic Usage ➡️ `git status`
- Shortened Status ➡️ `git status -s`
- Untracked Files ➡️ `git status --untracked-files=all`
- More Options
    - `--porcelain` ➡️ Provides machine-readable output suitable for scripting.
    - `--branch` ➡️ Shows the current branch and any tracking information.
    - `--long` ➡️ Offers a more detailed status report, including the exact changes made to modified files.

## git commit 👇
- `git commit` command is fundamental in Git for capturing snapshots of your project's history. It creates a new commit object that stores the current state of your tracked files along with a descriptive message.
- Basic Usage ➡️ `git commit`
- Specifying Commit Message ➡️ `git commit -m "Your commit message here"`
- Committing All Staged Changes ➡️ `git commit -a`
- Amending the Last Commit ➡️ `git commit --amend`
- get additional changes to a not pushed commit ➡️ `git commit –amend –a`
- Adding Untracked Files ➡️ `git commit -m "Your message" new_file.txt`
- More Options
    - `--date=<date>` ➡️ Sets the commit date explicitly.
    - `--no-verify` ➡️ Bypasses pre-commit hooks (if configured). Use with caution.
    - `--signoff` ➡️ Adds a GPG signature to the commit.

## git push 👇
- `git push` command is used to upload local commits to a remote repository. It's the counterpart to `git fetch` (downloading changes) and often used after you've made and committed changes locally.
- Basic Push ➡️ `git push origin main`
- Pushing Specific Branch ➡️ `git push origin main`
- Force Push ➡️ `git push origin main --force`
- Pushing Tags ➡️ `git push origin <tag_name>`
- More Options
    - `-u` ➡️ Sets the upstream branch for your current local branch. This simplifies future pushes as you won't need to specify the branch name each time.
    - `--dry-run` ➡️ Simulates the push process without making any actual changes. Useful for verifying what would be pushed.
    - `--delete` ➡️ Deletes a remote branch after pushing if it has been deleted locally
- push commits to server ➡️ `git push origin HEAD:<branch_name>`

## git log 👇
- `git log` command is your historian in the world of Git. It unveils the chronological record of your project's development by displaying a list of commits.
- Basic Usage ➡️ `git log`
- Show a one-line summary for each commit ➡️ `git log --oneline`
- Show visual representation of the commit history using ASCII art ➡️  `git log --graph`
- define a custom format for the commit messages using placeholders ➡️ `git log --pretty=format:<custom_format>`
    - print latest commit ID ➡️ `git log -1 --format=%H`
- Filtering Commits
    - Limiting Output ➡️ `git log -n <number>`
        - history of last 3 commit ➡️ `git log -3`
    - Author Filtering ➡️ `git log --author="John Doe"`
    - Grepping Commit Messages ➡️ `git log -S"<search_term>"`
    - Range Selection ➡️ `git log <commit_hash1>..<commit_hash2>`
        - print commits merged between two commits ➡️ `git log --oneline 1223344556677890897867453423122334456778..6523456789236734562354237856345634567890`
- More Options
    - `--all` ➡️ Shows commits from all branches, not just the current one.
    - `--topo-order` ➡️ Displays commits in a topological order (useful for complex branching).
    - `--stat` ➡️ Includes statistics about file changes in each commit.

## git rebase 👇
- Git rebase is a powerful tool for rewriting your commit history. It replays a series of commits on top of a new base commit.
- Basic Rebase ➡️ `git rebase <branch_name>`
- Interactive Rebase ➡️ `git rebase -i <branch_name>`
- More Options
    - `--onto <upstream> <branch_name>` ➡️ Rebases your current branch onto a specific upstream branch, useful for complex branching scenarios.
    - `--keep-base` ➡️ Maintains the original base commit of your branch instead of rebasing on top of the specified branch.
- rebasing steps
    - `git fetch`
    - `git rebase <branch_name>`
        - if any conflicts during rebase, then resolve and execute below comments
            - `git add .`
            - `git rebase --continue`
    - `git push --force-with-lease origin HEAD`

## git stash 👇
- `git stash` command acts as a temporary storage locker for your local changes in Git. It allows you to save your uncommitted work (modified files, staged changes, and even untracked files) on a stack for later retrieval, effectively taking a snapshot of your current working directory.
- Basic Usage ➡️ `git stash`
- Creating Stashes with Message ➡️ `git stash "Meaningful message"`
- Include Untracked Files ➡️ `git stash --include-untracked`
- Retrieving a Stash
    - Apply (Without Removing from Stash Stack) ➡️ `git stash apply <stash_id>`
    - `git stash apply` ➡️ to apply the most recent stash.
    - Pop (Apply and Remove from Stash Stack) ➡️ `git stash pop <stash_id>`
- Listing Stashes ➡️ `git stash list`
- More Options
    - `--keep-index` ➡️ Keeps the staged changes in the index even after stashing. This can be useful if you want to keep them staged while working on something else.
    - `--show` ➡️ Shows the details of a specific stash, including the diff of the changes it contains.
    - `--drop` ➡️ Removes a stash from the stash stack without applying it.
- `git stash show` ➡️ to see what n is in the below commands.
- `git stash apply stash@{n}` ➡️ to apply an older stash.

## git clean and git reset 👇
- clean repository ➡️ `git clean -xffd`
- reset repository ➡️ `git reset --hard`
- discard modified files and remove untracked files ➡️ `git reset --hard && git clean -f -d`
- remove last commit or uncommit last commit ➡️ `git reset --hard HEAD~1`

## git submodule 👇
- add submodule ➡️ `git submodule add https://github.com/chaitu-ycr/git_notes.git`
- add submodule in specific path ➡️ `git submodule add https://github.com/chaitu-ycr/git_notes.git path_to_store_submodule`
- force update submodules recursively ➡️ `git submodule update --init --recursive --force`    
- clean submodule recursively ➡️ `git submodule foreach --recursive git clean -xffd`
- reset submodule recursively ➡️ `git submodule foreach --recursive git reset --hard`
- remove submodule
    - remove the submodule entry from .git/config ➡️ `git submodule deinit -f path/to/submodule`
    - remove the submodule directory from the superproject's .git/modules directory ➡️ `rm -rf .git/modules/path/to/submodule`
    - remove the entry in .gitmodules and remove the submodule directory located at path/to/submodule ➡️ `git rm -f path/to/submodule`

## create/remove git tag 👇
- `git tag` command is used to create lightweight or annotated tags that act as bookmarks for specific points in your commit history.
- Creating Tags
    - Lightweight Tag (Reference to a Commit) ➡️ `git tag <tag_name> <commit_hash>`
    - Annotated Tag (With Message and Signature) ➡️ `git tag -m "Your message here" <tag_name>`
- Listing Tags ➡️ `git tag`
- Viewing Tag Details ➡️ `git show <tag_name>`
- Deleting Tags ➡️ `git tag -d <tag_name>`
- delete the old tag from remote origin ➡️ `git push origin :refs/tags/<tagname>`
- Pushing Tags to Remote Repository ➡️ `git push origin <tag_name>`
- push all new local tags to remote ➡️ `git push origin --tags`
- More Options
    - `-l` ➡️ Lists tags with additional information like the tag message (useful with `git tag`).
    - `--verify` ➡️ Verifies the GPG signature of an annotated tag (if applicable).
    - `--signed` ➡️ Creates a signed tag using your GPG key by default (shortcut for `-s`).

## git cherry-pick
- `git cherry-pick` command allows you to selectively apply specific commits from one branch to another branch in Git. It essentially "picks" a commit from a branch and grafts it onto your current branch, creating a new commit in your current branch history.
- Basic Usage ➡️ `git cherry-pick <commit_hash>`
- Resolving Merge Conflicts
    - If conflicts arise, Git will halt the cherry-pick process and present you with the conflicting parts of the code. You'll need to manually resolve these conflicts using your text editor and then stage the resolved files using `git add` before continuing with `git cherry-pick --continue`.
- Cherry-pick with Commit Message Editing ➡️ `git cherry-pick -e <commit_hash>`
- Skipping Conflicts ➡️ `git cherry-pick --skip <commit_hash>`

## increase push/pull timeouts 👇
- `git config lfs.dialtimeout 3600`
- `git config lfs.activitytimeout 3600`
- `git config lfs.tlstimeout 3600`
- `git config lfs.keepalive 3600`

## other useful git commands 👇
- open a graphical user interface showing only the mainline you are working ➡️ `gitk`
    - open a graphical user interface showing all branches ➡️ `gitk --all`
- compare your current changes on workspace (which are not committed yet) to the latest commit ➡️ `git difftool`
- if you want to compare the changes between 2 commits use ➡️ `git difftool <commit id 1> < commit id 2>`
