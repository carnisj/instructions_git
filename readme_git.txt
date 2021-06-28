To configure git bach to start in specific folder, add this line in .bashrc:   cd C:/Users/carnis/Work\ Folders/Documents/myscripts/bcdi/

Start folder:  
cd C:/Users/carnis/Work\ Folders/Documents/version\ control/reflections
cd C:/Users/carnis/Work\ Folders/Documents/myscripts/
cd C:/Users/Jerome/Documents/myscripts  on Dell precision
Setup to launch notepad++ from bash:
echo 'alias subl="C:/Program\ Files/Sublime\ Text\ 2/sublime_text.exe"' >> ~/.bashrc

On windows command line: FC filename_old filename_new
On git bash or Mac, Linux: diff -u filename_old filename_new
In git: git diff filename_old filename_new


Usefulness of having an history of a file:
	- test new ideas starting from a working version
	- debugging
User decides when saving:
	- best for me
To see the difference between two commit versions in git:
	git diff filename_old filename_new
How to decide when committing: think to the person trying to understand what you did.

To get colored diff output, run git config --global color.ui auto

git log --stat to see commits id and which file was modified
To stop viewing git log output, press q

To clone a repository, run git clone followed by a space and the repository URL.

Configure the proxy:

You can configure these globally in your user ~/.gitconfig file using the --global switch, or local to a repository in its .git/config file.
Setting a global proxy

Configure a global proxy if all access to all repos require this proxy

git config --global http.proxy http://proxyUsername:proxyPassword@proxy.server.com:port

check older version: git checkout commit_id

go to git home directory:  cd ~

Setup git to use notepad++ as text editor:
git config --global core.editor "'C:/Program\ Files\ \(x86\)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"

Add file to the stage:  git add filename
Remove file from the stage:  git rm --cached filename

Committer: CARNIS Jerome <CARNIS@esrf.fr>
git config --global user.name "Your Name"
git config --global user.email you@example.com

Commit: git commit -m "Commit message"
        git commit     (will open notepad++)
		
git diff (without filenames) to see the difference between the staging area and the working directory
git diff --staged (without filenames) to see the difference between the staging area and the previous commit

git reset --hard to discard any change in the working directory or the staging area

git checkout master    to leave 'detached HEAD' state

git branch newbranchname  : to create a new branch
git checkout newbranchname   : to change to the new branch
or the same in one command: git checkout -n newbranchname

git log --graph --oneline master coins

Merge branches into master:
git checkout master
git merge master coins
if error message:
git merge --abort
Solve newline problems in Windows
git config --global core.autocrlf true

Compare a commit with its parent:
git show commit_id

caching GitHub password in Git

Create a remote depository for Git Hub (named origin)
git remote add origin git@github.com:carnisj/CDI_preprocessing.git

Push a branch into GitHub repository: git push origin master

Check fetch and push adresses: git remote -v

Remove a remote repository named origin: git remote rm origin 

Pull commits from GitHub to local repository:  git pull origin master    git pull = git fetch + git merge

Update the local copy of GitHub repository: git fetch origin

List all remotes:              git remote -v
Remove a remote and references from local repository:  git remote rm remote_name

List all branches:             git branch -a
Delete remote branch:          git push --delete <remote_name> <branch_name>
Delete local branch:           git branch -d <branch_name>           use option -D instead of -d for force deleting the branch (irrespective of its merged status)

Merge the master into another branch:
git checkout branchname
git merge master branchname

Make a branch the new master:
git checkout better_branch
git merge --strategy=ours --no-commit master
git commit          # add information to the template merge message
git checkout master
git merge better_branch             # fast-forward master up to the merge

Delete the last not pushed commit (will lose all later modifications):
git reset --hard origin/master

git config --global credential.helper wincred
check for existing ssh keys ls -al ~./ssh
ssh-keygen -t rsa -b 4096 -C "carnis_jerome@yahoo.fr"    # create key
eval $(ssh-agent -s    # launch ssh agent
ssh-add ~/.ssh/id_rsa    # add the new key to the agent
clip < ~/.ssh/id_rsa.pub    # copy the key to the clipboard

Add an existing repository to GitHub:
	- create a new repository on GitHub
	- on the local computer, git init in the project root
	- git add .   # adds the files and stages them for commit
	- git commit
	- git remote add origin remote_repository_URL
	- git push origin master

to mark release points
git tag v1.4-lw
git tag -a v1.4 -m "my version 1.4"
git push origin --tags  or  git push origin v0.0.1
remove a tag locally: git tag -d v0.0.1
remove a remote taf: git push --delete origin v0.0.1


############################################
# Sync a fork with the original repository #
############################################
# Add the remote, call it "upstream":

git remote add upstream https://github.com/whoever/whatever.git

# Fetch all the branches of that remote into remote-tracking branches

git fetch upstream

# Make sure that you're on your master branch:

git checkout master

# Rewrite your master branch so that any commits of yours that
# aren't already in upstream/master are replayed on top of that
# other branch:

git rebase upstream/master
