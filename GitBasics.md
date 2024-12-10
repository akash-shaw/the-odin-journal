
# Git Basics

### Installation
Follow [these instructions](https://www.theodinproject.com/lessons/foundations-setting-up-git), no need to remember.

### Getting Started
```bash
git clone git@github.com:USER-NAME/REPOSITORY-NAME.git	#clone repo
git status	#status of git
git log	#shows recent commits
git add <path> #add files to staging area
git add .	#add everything to staging area
git commit -m "Commit Message"	#commit changes
git push	#upload changes
git pull	#up-to-date repo if web is ahead
```
### Danger Zone
```bash
#delete last commit
git reset --hard HEAD~1
git push origin +HEAD

#reverting back to a commit
git revert <commit_hash>..HEAD
git push origin main
```
### Working with Branches
```bash
git branch <branchname>		 #create new branch
git checkout <branchname>	 #switch branches
git checkout -b <branchname> #create and switch
git branch -a				 #list all branches
git branch -d <branchname>	 #delete branch

#merging branches
git checkout <target-branch>	#eg. main
git merge <source-branch>		#eg. dev
#NOTE: git merge will merge source-branch to the brach we're currently in
#NOTE: merge conflicts may arrive, solve them and then merge

#deleting local branch
git branch -d <branch-name>	#when already merged with main
git branch -D <branch-name>	#when not merged with main

#remote branches
git push origin <branch-name>	#push new branch
git push origin --delete <branch-name>	#delete remote branch

#renaming branches
git branch -m <new-branch-name>		#current branch
git branch -m <old-name> <new-name> #any branch

#save changes without committing
git stash
git stash apply		#apply stashed changes
```
---
This is all that I have used in my projects so far. As I discover new useful Git features, I'll update this list. I'm sure this will need to be updated quite often since I'm still fairly new to Git.