# Github tutorial

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

## Making branches