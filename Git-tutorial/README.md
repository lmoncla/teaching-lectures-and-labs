# Git tutorial and introduction

February 1, 2024

## Making a repository 

1. Let's start out by making a repository. The easiest way to make a fully new repository is to make one online and then clone it. You can also make a new remote repository from one that is on your laptop already, but we'll start with the first option. Navigate online to your Github profile. Click on the button to make a new repository, give it a name, description, and click on `Add a README file`. Then click on `Create Repository`. You now have a remote repository. 

2. Now, we need to get this repository onto our local machine. The easiest way to do that is to clone it. Click on the large green button that says `Code`, and copy the link. 

3. On your laptop, open terminal, navigate to a directory you would like to keep this in, and type `git clone` and then paste in the link you copied earlier. It is now there! 

4. `cd` into that directory and type `ls -a`. This tells your computer to list all files, including the hidden ones. Notice that there is a hidden directory in this folder called `.git`. This `.git` folder contains a bunch of other information about your repository as marks it as a git repository. Let's take a look at the config file. `cd .git/` and then `nano config`. We can see that there are all sorts of interesting pieces of information in here. We can see that this local repository is now linked to a remote repository that is called the `remote origin`. In git parlance, `origin` is shorthand for the remote repository (the url) that the local repository was originally cloned from. Labeling this url as "origin" just makes all the paths easier to type and look at. The other files contain other information that we don't need to worry about right now, but you can explore all of these, and they can be handy for when something goes wrong. 

## Making changes and pushing them 

5. Now let's make a change to our README and push that change to github. To start off, open your file `README.md` in a text editor and type some sentences into it. They can be whatever you want, it doesn't matter. To get this change onto github, we need to do the following 3 commands: 

a. `git add README.md`: this tells git to stage this file and start tracking it. Now, type in `git status`. You can see that the README is logged as modified! We also get some other useful information. For example, we are currently on the `main` branch. Because we haven't made a commit yet, our local `main` branch is currently up to date with the remote `main` branch, also called `origin/main`.  
 
b. `git commit -m "adding content to the README"`: You are now making a commit to git. This is change you would like to log in the file's history. Every time you make a commit, git makes a checkpoint for that file version, and records your commit message in it's history. It's best to make these messages informative, because it will help future you figure out and remember what you were doing and why you were making these changes. Once you make the commit, run `git status` again and check it out. We see now that my main branch is ahead of the remote main branch by 1 commit, the commit we just made. 

c. Now, the final step is to push this change to the remote repository. To do this, run `git push`. You should now see your edits online! 

5. Practice this by doing this 2 more times, making 2 more commits and pushes. 

## Using the version control aspect of git: looking at old versions and reverting to them

6. Let's say now that we instantly regret our most recent commit, and somehow this totally messed up our repository. It would be easy to just make a new commit that deletes that last commit, but in real life, maybe we edited a ton of lines and don't know where our mistake is. Let's say that our last commit was really complicated and we just want to go back in time by 1 commit. We have a couple of options: we can go back to the old commit and take a look around our files from that checkpoint, or we can completely reset to that old timepoint. We will now do the first, then the 2nd. 

7. Poke around our previous timepoint: Let's start out by looking at our commit history: `git log`. Notice that a complete history of all our commits is printed out, and that each commit has a hash, or a string of text and numbers. This hash gives us a little tag for each commit that we can use to travel back in time to and older commit. To do so, do `git checkout HASH` where `HASH` is the very long alphanumeric HASH that follows `commit`. Look at your README file on your laptop. It is now reverted to the version it was at at the previous commit. We can exit this by typing `git switch -`. The file now is back to being what it was. Notice that for this step, nothing has changed on remote. That is because we are just checking out and going back and forwards in commits locally. 

8. In order to revert on remote, we need to do another step, which is to reset our branch to a previous checkpoint. Again, use `git log` to figure out the HASH of the checkpoint you want to revert to. Now, type the following: `git reset --hard HASH`. This resets your local tree to HASH. Then, `git push -f origin main` to push to remote. Check online, and see that it is now reverted! This fully gets rid of any commits that happened afterwards, so it is destructive. There are other options available if you want to retain them. 

## Making and merging branches
9. Now let's practice making a branch. Branches are useful for developing new features, and are especially useful when you'd like to make major changes and want to test them out before deploying them. Let's start by printing out our current branches wit `git branch -a`. You should see that currently, we only have one branch, `main`. To make a new one, type `git branch NEW-BRANCH-NAME`. Use `git branch -a`to check that you made it. Then, switch to it, with `git checkout NEW-BRANCH-NAME`. Now if you check again, see that we are now on our new branch! 

10. Let's make a new commit to our `README.md`file on our new branch. Edit your file however you want, and make a new git add, and git commit. 

11. Notice that at this point, your branch is not yet on remote. It currently only exists on our local. To push it to remote, we need to `git push origin NEW-BRANCH-NAME`. Origin tells git that we are pushing this branch to our remote, and that we want to make a new remote branch name with the same branch as our local, NEW-BRANCH-NAME. Notice now that online, the new branch exists! Also, if we type `git branch -a` into terminal, we now see our new branch listed as a remote branch.  

12. One funny thing about git is that the version of your files that you see on your laptop changes depending on the branch you are currently on. Take a look at your README on your laptop, then switch back to your main branch by typing `git checkout main`. Now look at your README. It changed! That is because git shows you the file version of the branch it is on. 

13. Let's pretend now that we are done editing on this branch, and we would like to add in our new edits into our original file. To do that, we need to merge our branch into our main branch. To do this, switch back to `main` branch with `git checkout main`and then merge with `git merge NEW-BRANCH-NAME`. You'll see a message that git merged by fastforwarding. To push this to remote, simply do `git push`. You can now see that now the merge is on github. Finally, since we are done with this branch, we can delete it with `git branch -d NEW-BRANCH-NAME`. It is now deleted. 


## Working on a file collaboratively, and solving merge conflicts
14. One of the most useful things about git is that it allows you to collaborate with other people. For example, say we have a file that we all need to use (for example, annotations on bird types, or information on using pMACS). In these cases, it makes sense to have one central file that everyone can edit. Git is perfect for this. Go to https://github.com/moncla-lab/github-collaboration-demo, and clone this repository into a new directory on your laptop. We are now going to have multiple people make edits to it, and deal with a merge conflict. 

15. One person should now make a commit, or set of commits. Add people, reorder them, whatever you want. Push to remote. 

16. Now, say I am also using this file. The best practice thing to do is to gather any new commits that others have made before I start my work. To do that, I can do `git pull`. Everyone should do that now. This will pull all of the work that has happened on remote onto your local branch, thus saving you from having to redo it. 

17. Let's say now that you also want to add information into the file. We don't always know who else in working on these files, potentially at the same time. Things can get messy when people try to merge work onto the main branch on remote at the same time. The best practice way to avoid these issues is to create a new branch, add your edits to that branch, push to remote, and then merge via Github on remote as a pull request. So, do the following: 

a. After pulling, make a new branch with `git checkout -b BranchName`. This is a shortcut for making a new branch and switching to it. 
b. Add your edits to the file. Commit them, and push the branch to remote: `git push origin BranchName`
c. Now, we are going to pick one person to merge into main, and then the next person will do so. In some cases, when two people are pushing to the same file and making conflicting edits, you can run into "merge conflicts". In these cases, git cannot figure out by itself how to reconcile the changes, so you have to interactively reconcile the changes. To do so, create a pull request, fix merge conflicts, and submit the pull request on Github. Make sure you are merging branch into main. 


## What if you messed up and forgot to pull and then committed to main??
If you did this and had a significant number of changes, you're going to have to do a rebase, which is sort of confusing. Let's say though that I forgot to pull and instead started working on the file on my own. Sometimes this happens if you wait awhile to commit, or skip a commit, and someone else works on the project without you. 

`git pull --rebase`

fix the merge conflicts.  

`git add`, `git commit -m`, and `git push`. Then, exit the rebase with `git rebase --continue`. 

**[additional information on merge conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line)**


**git log --graph --all**

## Additional notes on permissions

One of the more confusing aspects of git and github are permissions issues, and these have gotten especially weird ever since git required the use of 2 factor authentication. I know that multiple people in the lab have had issues with pushing to repos, and Anna and I were troubleshooting this recently, and we figured it out. It turns out that this is likely due to 2 factor authentication issues. To overcome the issue, we did the following:

1. Follow instructions in your terminal for setting up 2 factor authentication. You will have to go online and use a QR code to set this up. I use Duo, and this works fine.

2. Then, this is quite confusing and not at all specified, but you also have to set a personal access token. Follow instructions to do that, which are outlined here: https://docs.github.com/en/enterprise-server@3.9/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens

3. Once you've done that, you're ready to try to push again. When prompted on the command line for a username and password, enter your Github username and your personal access token instead of the password. I have no idea why the message does not specify that you need to use your token, but this is what you need to do. You should only have to do this once, and then you should be set! 

* to troubleshoot this, we generally followed this article/set of instructions: https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/accessing-github-using-two-factor-authentication





