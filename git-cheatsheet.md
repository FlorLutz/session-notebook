# Git commands

- **git init** : make current folder a git repo (not inside another git-repo!)
- **git status** : show status of repo
- **states that can be output** : untracked (not part of git), modified (changes dince last commit), staged (to be included in next commit), committed (changes saved in git)
- **git add .** : add all files to repo
- **git add <filename>** : add file to stage
- **git commit -m "_commit name ex initial commit_"** : commit all staged files
- **git log --oneline** : show the commit history
- **q** : escape the oneline log
- **git restore .** : return to last commited state
- **git restore <filename>** restore individual files
- **git remote add origin git@github.com:GitHubUsername/repository-name.git** : connecting local repo to a new repo (after creating the repo in github.com) AND
- **git remote -v** : show ssh for fetch and push as test if it worked
- **git branch -M main** : make it the main branch AND
- **git push -u origin main** : push commitments, to be repeated after all commits
  (remember the 3 steps to push are add (files to commit), commit (them to the local repo) and push (them online to github))
- **git clone <url>** : cloning a remote repo, use the SSH-url!
  or rename a file
- **git push** : upload content
- **git pull** : download content

##branches

- **git switch -c "feature-branch"** : open new side branch and go there
- **git switch -** : go to main branch
- **git branch** : shows all branches
- **git branch -a** : list all branches - local and remote
- **git branch -d "branchname"** : deletes a branch
- **git push -u origin "branchname"** : pushes a particular branch, after used once, can be done again with **git push**
- **git pull origin main** : pulls a main branch from GitHub (like after merging)
