# How to undo changes made in git

Consider git history when undo changes made


## Modifying the last commit
***
### To modifiy commit message
Use `git commit --amend` to modify commit message. However this changes the git commit hash too. It means **it changes git history** as well. This cause a problem to other people's git history. 
> ```bash
> $ git commit --amend -m "modified message"
> ```

### To include staged files to the last git commit.
`git commit --amend hash` adds staged file to the last commit(changes git history(hash))
> ```bash
> $ git commit --amend 
> ```


## Undoing changes
***
> * git checkout
> * git reset (soft, default, hard)
> * git cherry-pick
> * git revert


### To undo changes made in directory
`git checkout filename` let you go back to the last commit state. 
Any changes made on that file will be gone and there is no way to undo this. 
> ```bash
> $ git checkout filename
> ```


### To undo commit
Use `git rest` to undo commits made. There are three types of reset
> ``` bash
> $ git reset --soft 
> $ git reset --mixed (default)
> $ git reset --hard 
> ```
### How to select commit hash code
If you want to go back to commit C, then use commit hash of B

> ```
> # git log
> 
> │   commit A
> │   commit B
> │   commit C
> │   commit D
> ```

### `git reset --soft hash`
Soft resets us back to the commit we specified, but **it keeps our changes that we made wihin staging area.** 
> ```bash
> $ git reset --soft hash
> ```

### `git reset --mixed hash`
Files changed are not in staging area, but **it's in working directory**
> ```bash
> $ git reset hash
> ```

### `git reset --hard hash`
All of our tracked files match the state that they were in at the hash we specified. This gets rid of your changes.
It reverts all of the tracked files back to the state they were, but it leaves any untracked files alone
> ```bash
> $ git reset --hard hash
> ```

### To get rid of untracked file
Use `git clean' to delete untracked files and direcotry. It deletes files as well. 
> ``` bash
> git clean -df # -d for directory, -f for files
> ```


### When commited to a wrong branch.
Supposed that you needed to commit to a feature branch, but accidentally commited to the master branch.

Let's move a commit made on master to the feature branch

Use `git cherry-pick` to move commit made on master to feature branch
`git cherry-pick` does not delete a commit, so you need to manually remove commit on master at the end with `git reset`.
> ```bash
> $ git checkout master (go to master first)
> $ git log (copy commit hash you want to move)
> $ git checkout feature (switch to feature branch)
> $ git cherry-pick hash
> ```


## `git revert` and managing git history
It is not recommanded to change git history(commit hash) because it can mess up other people's commit history if they have pulled those changes already. 

### `git revert`

It creates a new commit to reverse the effect of some earlier commits so this way you don't rewrite any history. **It's not going to modify or delete our existing commits** that you've made. It's going to **create a new commit** on top of the commit you want to delete/modify and it will undo all of the changes so that our history remains intact.

It does not delete a commit, which is safe in terms of not changing git history.

> ``` bash
> git revert hash
> ```
