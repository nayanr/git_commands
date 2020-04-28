# Useful Github Commands

##### Creating an Alias

Previously if needed a command like below:
``` git log --oneline --graph -- decorate ```
Now we can make an alias for it
``` git config --global alias.hist "git log --oneline --graph -- decorate" ```

where hist is our alias-name 
This helps us to save from writing always the commands we use most often.

To get list of all global configuration settings
``` git config --global --list ```

##### Renaming and deleting file

``` git mv currentfilename newfilename ```

##### Seeing differences

``` git diff ``` or if we have a configured difftool like p4merge ``` git difftool ``` can be used to see the differences between two commit points, or HEAD and a an earlier commit point

``` git diff some_commit_point_extracted_from_git_log HEAD ``` 

##### Branching and Merging

HEAD - points to the last commit in the working branch
Feature Branches are usually merged with the master branch, this can happen automatically if no conflicts arise or if conflicts arisie they can be manually resolved and a merge commit point is created in the master branch !!
To list all the  branches and the current branch
``` git branch -a``` 
``` git branch ``` 
To create a new branch
``` git checkout -b branchname ```
git diff can be used to compare two branches too :)

to switch branches use checkout
``` git checkout branchname ```

to merge a branch to current branch
``` git merge branch_to_be_merged ```

to delete a branch post usage 
``` git branch -d branchname ```

##### Resolving Conflicts While Merging 

Using mergetool seems a good option to resolve conflicts manually

##### Making special events with tagging

Simple tag creation - tags are created just to show some special point during development

``` git tag mytag ```
``` git tag --list ```
``` git tag -d mytag ```
To store some major milestone or a version release for say we use annotated tags
``` git tag -a v1.0 -m "Release 1.0" ```
To display info can use
``` git show v1.0 ```
and we would get the details and messages related to the tag !!


##### Stashing -  Saving work in progress

When you want to revert back but also store the new changes made just so that you can use them again :)

``` git stash ```
It saves the working directory and index state.

``` git stash list ``` 
to show all the stashes made and stored

Usually we go back to our repo do the changes needed, come back and then pop the stash and we get the changes we did before !!

``` git stash pop ```
It applies the stash and remove it from the stash list .

##### Time travel with reset and reflog
Reset to a particular commit-point
three types soft,medium and hard

``` git reset commit-id --soft ```
``` git reset commit-id --mixed ```
``` git reset commit-id --hard ```
soft takes us to that commit point but also stores the changes made in working directory and staging area currently, it just changes the head position

mixed doesn't have anything in the staging area 

hard ignores all - destructive reset mode, any changes pending is dropped

git log --oneline lists only last commits

``` git reflog ```
reflog shows all the commits we have done in the working directory and we can have our history once we make a hard reset

#### Github

Most popular Git Hosting, free public repositories



###### Adding a remote repositories 

``` git remote -v ```
lists if remote repositories are connected

``` git remote add origin url ```
to add a remote repository

###### For Pushing

Pushing up, sending all the tags too 
``` git push -u origin master --tags```

###### Authentication using ssh-key

https requires username and password each time.
use ssh setup to avoid this step each time on your local machine.

##### Github Clone Command

``` git clone repo-url ```
clones into a directory named as the repo name itself
``` git clone repo-url direcory-name-you-want ```
for a different name use above command.

After cloning repo and doing all the changes locally push changes back

##### Publishing changes back

``` git config --global push.default simple ```
this sets to push on all branches if we use
``` git push ```

#### git fetch and pull

If remote repo is modified when we are working locally a push may run into error and suggests to fetch first

Pull actually fetches and merges that with local

``` git fetch ```
fetches changes happened

``` git push ``` would work if no conflicts are present and would merge

``` git pull ```
if git fetch command returns some changes it will be shown while doing a git status if it could be merged use a git pull


###### If we change the repository name in github we need to change the refernce locally too

``` git remote set-url origin url ```

``` git remote show origin ```

##### Github time trvel 

go in commits tab and select symbol to go to the point in time when that commit, browse files and after all this return back to master

copy sha1 for that commit to see locally

``` git show sha1_code_here ```

##### Comparing and Pull requests

Compare with other branches on github, if merge is possible we can create pull request and this will be left for approval. 

Place a pull request with the owner and after approval it will be merged !!


##### Merging locally

``` git merge branchname tobemergebranchname ```

``` git fetch -p ```
prune dead branches locally

##### Locally switch to a branch on github

```
git fetch
git branch -a
git checkout remote_branch
```
``` git pull --all ```
this pulls all the branches being tracked locally


###### To push a branch deletion on Github

``` git push origin :branchname ```
after deleting it locally

##### Pull with rebase

concept of rebasing -- 

reabse is basically stating that we want our commits to be always ahead of what happened on remote in github, so we pull with rebase

``` git pull --rebase ```

#### Github Graphs

``` git log --oneline --graph ```

or we can go to github and check graphs tab directly

##### Setting default branch

default branch option in settings of repository 
any clone will clone default branch

##### Pull conflict
between remote and local


##### Github allows use of release notes with tags used

##### Tags in local

``` git log --oneline ```
``` git tag ```
Simple light weight tags, simply labels a sepcific position like below we are creating a tag unstable at the point of last commit in the branchname

``` git tag unstable branchname ```
``` git tag --list ```

Example of annotated tag
``` git tag -a v0.1-alpha -m "release 0.1" commitid ```
``` git show ```

###### Pushing local tags to github

``` git pull ```
``` git push ```

By default tags are not pushed

``` git push origin tagname ```
origin points at github

``` git push --tags ```
to push all the tags
On github we can add release messages related to the github

##### Deleting tags

On github we can just go to releases tab then tag and click on the tag to expand and select the delete option.

Locally we can delete

``` git fetch -p ``` to sync and prune dead stuff

``` git tag -d tagname ```
``` git push origin :tagname ``` to delete it from remote too

##### Updating tags (floating tags)

Moving tags to new commit id

``` git tag -f tagname commitid_to_be_associated ```
``` git push --force origin tagname ``` to update tags on remote simple ``` git push origin tagname ``` runs into error


Can use the pre release function while editing releases on github.

Deleting a release doesn't delete the tag, need to delete from the ta section too.

To create a new release on github use draft a new release option from releases tab.

##### Comparing with pull requests on github

Create a new pull request takes us to compare option and we can compare branches

Comparing commits can be done under commits tab
can also be done using pull request comparing with a branch.

Tags can also be doing using pull request comparing.

branch@(time) can be used to compare between different positions.

##### Social Coding

Forking a github repository.
Up-stream repository is the repo forked from !!

Create a feture branch after cloning into local the forked repository.

Push the feature branch to remote on github.

Creating a pull-request.
This for submitting our contributions to the upstream repository !!

Open a pull request opens it with the directory forked from !!
Reverting and restoring pull requests is also allowed on github !!

Syncing changes back to fork --

To add parent repo in local for pulling changes use 

``` git remode add upstream url_of_parent ```
``` git remote -v ```
to list all theremote repos connected

``` git pull upstream master ```
upstream just works as origin but points to the upstream directory

``` git push origin master ```
pushes changes to our fork












