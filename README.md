# Lab03: Git and GitHub

The goal of this laboratory exercise is to learn more about the workflow involving Git/GitHub for version control both on the command line, through Git front ends such as Source Tree and via GitHub.

## Step 1. Creating a new repository on GitHub

First, we need to create a new repository on GitHub. Log into GitHub with the acocunt you've been using for this training. Click on the *Repository* tab. Next, the *New* button. Under *Repository name* give your new repository a name, such as `lab03-exercise`. Next, fill in a short description in the appropriate field. Make sure *Public* is selected because private repositories cost money. Then, make sure to select *Initialize this repository with a README*. Finally, select **Java** under *.gitignore*. Once you completed these steps press the *Create Repository* button. There, you've created your own repository.

Once you have finished creating your repository, copy the its URL using the *Clone* button.

## Step 2. Creating a git repository locally

First, using the terminal app, create a new, empty directory and change to that directory. So for example:

```bash
$ mkdir lab03-exericise
$ cd lab03-exercise
```

Next, initialize this directory as a local git repository. This action is done with the following command, inside the directory you just created above:

```bash
$ git init
```

The result of this command should look something like:

```bash
Initialized empty Git repository in /Users/aknight/lab03-exercise/.git/
```

Next, check the status of this repository. The following should look similar to what you see on your computer when you type the command `git status`:

```bash
$ git status
On branch master

Initial commit

nothing to commit (create /copy files and use "git add" to track)
```

## Step 4. Setting up your remote

As of now, the repository we created above only exists locally. What we'd want to do is associate with the remote repository you created in Step 1. To do that we need to tell git where the remote is located and then pull the repository down to our local repository. You should still have in your clip board the URL from cloning the repository you created. If you don't go back there now and re-copy that URL. Next enter the following commands in the terminal:

```bash
$ git remote add origin https://github.com/path_to_your_lab03/lab03-exercise

$ git remote -v
origin https://github.com/path_to_your_lab03/lab03-exercise.git (pull)
origin https://github.com/path_to_your_lab03/lab03-exercise.git (fetch)
```

Next, we'll create a file, empty for now, and then commit it. Something like this:

```bash
$ touch hello.groovy
```

Issue a status command. You should see something like this:

```bash
$git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	hello.groovy

nothing added to commit but untracked files present (use "git add" to track)
```

Next, we'll add that file, commit it and push it up to the repository. Your session should look something like:

```bash
$ git add hello.groovy
$ git commit -m 'First commit'
[master (root-commit) 24f3527] First commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 hello.groovy
```

Finally, we'll push these changes up to GitHub. The following should push the commits:
```bash
$ git branch --set-upstream-to=origin/master master
Branch master set up to track remote branch master from origin.

$ git pull --allow-unrelated-histories
Merge made by the 'recursive' strategy.
 .gitignore | 22 ++++++++++++++++++++++
 README.md  |  2 ++
 2 files changed, 24 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md

```
Then:

```bash
$ git push
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 573 bytes | 0 bytes/s, done.
Total 5 (delta 0), reused 0 (delta 0)
To https://github.com/ProfKnight/lab03-exercise-test.git
   347584a..7f2959b  master -> master
```

## Step 5. Diffing the changes

One last step to fully familiarize yourself with git workflow. Make a simple, or even complex change to hello.groovy. Then use git to tell you what the difference between what you commited last and what you have now. Issue the following command:

```bash
$ git diff hello.groovy
diff --git a/hello.groovy b/hello.groovy
index e69de29..a03be86 100644
--- a/hello.groovy
+++ b/hello.groovy
@@ -0,0 +1 @@
+println 'hello world'
```

Commit that change, without me telling you want the exact command is here in the lab write-up, and then make another change. Do the `git diff` command again and see what it says

## Step 6. Wrapping it up

That's it for now. I highly recommend reading a git and/or GitHub tutorial. I highly recommend [GitMagic](http://www-cs-students.stanford.edu/~blynn/gitmagic/) for git and [Git and GitHub learning resources](https://help.github.com/articles/git-and-github-learning-resources/) for GitHub
