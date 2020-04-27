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

##### Publishing chaanges back

``` git config --global push.default simple ```
this sets to push on all branches if we use
``` git push ```
