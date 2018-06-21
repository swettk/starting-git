# Setup
## SSH Keys in github (for those of you without yubikeys)
  * Authenticates your access to private repos
  * Is a key unique to you
  * Yubikeys will replace this once we get you setup

  ```
  ssh-add -L # If this has a value use this in github
  ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_goodeggs_rsa
  ssh-add ~/.ssh/id_goodeggs_rsa
  ssh-add -L # Put this key in github
  ```
  * Add your key to [github](https://github.com/settings/keys) after you've signed in
  * __Side note, I need everyone's github username to add as a collaborator__

## Clone a repo
  * [This Repo](https://github.com/swettk/starting-git)
  * This gives you a **LOCAL** copy to your workstation
  * Creates a new **REMOTE** with a special name of `origin` (all you need for our use case)
  * We are NOT creating a **FORK**, everyone has permissions on the main repo

# Daily Tasks

## Do some work
  * If your work comes from pivotal, lookup your ticket #
  * **BRANCH** `git checkout -b your-branch-name`
  * `git branch` shows you the branch you're on
  * **ADD** **STAGES** your changes to the index
    * `git add <filename>`
  * `git status` shows you what files changed and what's on the index
  * **COMMIT** them to your branch
    * `git commit` logs your changes with a comment
  * `git diff` shows you what's different (origin/master, HEAD^, HEAD^^)
  * `.gitignore` files that don't need to be tracked

## Undoing a mistake
  * `git reset <filename>`
    * discard commits on a private branch (local) or throw away uncommited changes
    * with a filename unstages a file
  * `git checkout <filename>` undoes changes to latest commited version or point in history

## Share your work (Pull Request)
  * **PUSH** to github (Publishes your changes so others can see)
  * open a **PULL REQUEST**
  * Have a teammate do a code review
  * Make sure **CI** completes
  * Merge your **PR** after success!

## Cleanup
  * `git branch -D <branchname>` deletes a local branch
  * `git remote prune origin` cleans up your local tracking against `origin` -- after the remote branch was deleted following a pull request

## Pulling other's changes
  * `git remote show origin` shows you what's going on with the `origin`
  * `git fetch` Updates your clone get changes from `origin`
  * `git pull` shortcut to pull in the latest version of a tracked branch (on your current branch)
  * `git checkout -b <remotebranch> origin/<remotebranch>` Pulls in a branch somebody else shared

## Sometimes it's not so smooth
### Your branch is out of date (PR can't merge)
  * `git rebase master`
  * `git merge`
  * Resolving conflicts

## See what happened
  * `git log`
  * `git blame <filename>`
  * `git diff`

# Advanced topics
## Undoing a mistake you've shared
  * `git revert` -- replays history in reverse

## Multiple lines of work at the same time
  * `git branch`
  * `git stash`
  * `git checkout`

## Tagging points in time
  * `git tag`

## Steal single changes from other branches
  * `git cherry-pick <sha of change>`

## Handy History rewriting
  * `git rebase -i <your historical commit>`
  * `git push -f` force push (overwrite) to remote branch
  * `git commit --amend` don't create a new commit, just tack on to the previous
  * `git commit --allow-empty -m '<commit message>'` do an empty commit to trigger CI
