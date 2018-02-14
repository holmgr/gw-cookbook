# gw-cookbook
A small tutorial for Git

## Installation
To be able to complete this tutorial you will need to have installed Git on your own computer and setup the basic configuration.

Install Git: https://git-scm.com/

Setup username and email in Git:
```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

## Tasks
You are the publisher helping the famous GW Persson to publish his first cookbook, the next best seller surely!

However, there are some issues since GW can be a bit unsure and messy regarding his content. You therefor decide that you will need a non linear workflow and some powerful version handling. Git to the rescue!

If you get stuck on any task, please feel free to ask but also try to use the helpful: `git help <command>`, which will show you the flags and usage of a given command.
You can also look at the _Solutions_ section if you get stuck.

### Task 1
You will first need to _clone_ this repository to get your local copy to get started.
Use `git clone git@github.com:holmgr/gw-cookbook.git` to get a local copy.

Take a look in the `gw-cookbook` folder it created, can you see the recipes from GW and the `.git` hidden folder?

### Task 2
GW has realized that he will need some fish recipe also in his cookbook.
Create a new file in the folder called `lax.md` with the following contents:

```
# Lax
* 1/2 kruka basilika
* 1 dl crème fraiche
* salt
* peppar
* ca 500 g laxfilé
```

Check if you have some untracked files not added to the index, which command should you use?

Add the `lax.md` file to the index using the appropriate command. 

Then commit the new file to the git repository with the message `Add salmon recipe`

### Task 3
GW has realized that `lclf` is quite popular and decides that he may which to change some of his recipes to target that.
Create a new branch `lclf` and switch to it using the appropriate commands.

Check that you are really on that branch, which command(s) can you use?

Remove the _vispgrädde_  from his potatismos recipe.
Check you that your changes are correct using the appropriate command, which is it?

Add and commit the results with the message `Remove whipped cream`.

GW realizes that he also wants to reduce the amount of butter in his recipe.
Discard the last commit using `git reset --soft HEAD~`, what would be the difference if we would have used `--hard`?
Hint: Look at the current state of the index using `git diff --staged`

Reduce the _smör eller margarin_ in his potatismos recipe to 5msk, then add and check your changes.
Make sure that both the whipped cream will be removed and the butter will be reduced.
Commit your changes with the message `Reduce fat in potatismos`

### Task 4
GW wants to add another recipe whether or not he actually decides to use the `lclf` version.
Switch back to the `master` branch and create a new file `kyckling.md` with the following contents:

```
# Kyckling
600 g kyckling
1 st röd paprika
2 st gul lök
50 g smör
3 msk Curry
5 dl grädde
2 dl créme fraiche
2 msk soja
salt och peppar
1 msk paprika pulver
```

Add the file to the index and commit the results with the message `Add chicken recipe`.
Look at the difference between the `master` and `lclf` branches, what do you see?

### Task 5
GW has decided that he is happy with his changes in the `lclf` version and wants to use them in his final version.

Combine the changes from `lclf` by either using merge or rebase. Why would rebase be an okay choice here, when would it not be okay to use?

Remove the `lclf` branch using an appropriate command.

#### Task 6
Look at the history of the project by using `git log` (please use the flags provided).
Depending on whether you used merge or rebase you will see different results why?

## Solutions

### Task 2
* Show untracked files: `git status`
* Add files to index: `git add lax.md`
* Commit changes: `git commit -m "Add salmon recipe"`

### Task 3
* New branch: `git branch lclf`
* Switch branch: `git checkout lclf`
* Check branch: `git status` or `git branch`
* Check changes: `git diff`
* Add changes: `git add potatismos.md`
* Commit the results `git commit -m "Remove whipped cream"`.
* Discard changes `git commit reset --soft`, removes commit but sets index to what it was. Hard will clear index
* Add changes: `git add potatismos.md`
* Check that both files are present and changes are in: `git diff --staged`
* Commit changes `git commit -m "Reduce fat in potatismos"`

### Task 4
* Switch back to master: `git checkout master`
* Add changes: `git add kyckling.md`
* Commit changes: `git commit -m "Add chicken recipe"`
* Check diff between branches: `git diff lclf`

### Task 5
* With rebase: `git rebase lclf`, will be ok since we have not shared the branch with anyone and it will not be used any more.
* With merge: `git merge lclf`
* Remove branch: `git branch -d lclf` 

### Task 6
* Show history: `git log`, rebase will not result in a merge commit and non-linear timeline.
