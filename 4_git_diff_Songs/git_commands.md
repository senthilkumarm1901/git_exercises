# Git Diff Exercise

This exercise comes with a starter repo that you will need to clone down to your machine.  We will be working with two bands: Queen and Fleetwood Mac and their various lineups over the years.

## Part 1: Setup

Please run the following commands from your terminal.  Make sure you are not inside of a Git repo.

```
git clone https://github.com/Colt/git-diff-exercise
```

- Change into the newly created folder called `git-diff-exercise`.  You will be on a branch called `current` by default.
- Run `git switch 1970s`
- You should now have two branches that you can move between: `current` and `1970s` Each branch contains two files: `queen.txt` and `fleetwoodmac.txt`

>[!Note]

```bash
senthilkumar.m@terminalsec8_git-diff-compare-changes % git clone https://github.com/Colt/git-diff-exercise
Cloning into 'git-diff-exercise'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 15 (delta 1), reused 15 (delta 1), pack-reused 0 (from 0)
Receiving objects: 100% (15/15), done.
Resolving deltas: 100% (1/1), done.
senthilkumar.m@terminalsec8_git-diff-compare-changes % cd git-diff-exercise 
senthilkumar.m@terminalgit-diff-exercise % git branch -v
* current 09cbcc9 replace John Deacon as Queen's bassist
senthilkumar.m@terminalgit-diff-exercise % git branch -v --all
* current                09cbcc9 replace John Deacon as Queen's bassist
  remotes/origin/1970s   247e203 add early 1970s fleetwood mac lineup
  remotes/origin/HEAD    -> origin/current
  remotes/origin/current 09cbcc9 replace John Deacon as Queen's bassist
senthilkumar.m@terminalgit-diff-exercise % git switch 1970s
branch '1970s' set up to track 'origin/1970s'.
Switched to a new branch '1970s'
senthilkumar.m@terminalgit-diff-exercise % git branch -v
* 1970s   247e203 add early 1970s fleetwood mac lineup
  current 09cbcc9 replace John Deacon as Queen's bassist
```



## Part 2: The Diffs

1. Compare the difference between the `1970s` branch and the `current` branch across all files

```bash
senthilkumar.m@terminalgit-diff-exercise % git diff current..1970s
diff --git a/fleetwoodmac.txt b/fleetwoodmac.txt
index 653b184..6f44367 100644
--- a/fleetwoodmac.txt
+++ b/fleetwoodmac.txt
@@ -1,5 +1,5 @@
-Lead Vocals: Stevie Nicks
-Lead Guitar: Mike Campbell
+Lead Vocals: Jeremy Spencer
+Lead Guitar: Lindsey Buckingham
 Bass: John McVie
 Drums: Mick Fleetwood
-Keyboard: Christine McVie
\ No newline at end of file
+Keyboard: None
\ No newline at end of file
diff --git a/queen.txt b/queen.txt
index 0e0fa0d..2ab2d04 100644
--- a/queen.txt
+++ b/queen.txt
@@ -1,4 +1,4 @@
-Lead Vocals: Adam Lambert
+Lead Vocals: Freddie Mercury
 Lead Guitar: Brian May
-Bass: Neil Fairclough
+Bass: Mike Grose
 Drums: Roger Taylor
\ No newline at end of file
```

2. Compare the difference between the `1970s` branch and the `current` branch but only for the queen.txt file

```bash
senthilkumar.m@terminalgit-diff-exercise % git diff current 1970s -- queen.txt
diff --git a/queen.txt b/queen.txt
index 0e0fa0d..2ab2d04 100644
--- a/queen.txt
+++ b/queen.txt
@@ -1,4 +1,4 @@
-Lead Vocals: Adam Lambert
+Lead Vocals: Freddie Mercury
 Lead Guitar: Brian May
-Bass: Neil Fairclough
+Bass: Mike Grose
 Drums: Roger Taylor
\ No newline at end of file
```

3. Switch over to the `current` branch if you are not currently on it.   Run a diff to compare the current HEAD to the previous commit (you could use the commit hash or reference HEAD's parent commit)


```bash
git diff HEAD^ HEAD
# The command git diff HEAD^ HEAD compares the content changes between the most recent commit (HEAD) and its immediate parent commit (HEAD^).
```

4. While on the `current` branch, change the `queen.txt` file by replacing Adam Lambert with your own name.  Save the change.  Add `queen.txt` to the staging area.  DO NOT COMMIT YET!

```bash
senthilkumar.m@terminalgit-diff-exercise % git status
On branch 1970s
Your branch is up to date with 'origin/1970s'.

nothing to commit, working tree clean
senthilkumar.m@terminalgit-diff-exercise % git switch current
Switched to branch 'current'
Your branch is up to date with 'origin/current'.
senthilkumar.m@terminalgit-diff-exercise % cat queen.txt 
Lead Vocals: Adam Lambert
Lead Guitar: Brian May
Bass: Neil Fairclough
Drums: Roger Taylor%                                                                                                                                                senthilkumar.m@terminalgit-diff-exercise % vi queen.txt 
senthilkumar.m@terminalgit-diff-exercise % git add queen.txt 
senthilkumar.m@terminalgit-diff-exercise % cat queen.txt 
Lead Vocals: Senthil Kumar
Lead Guitar: Brian May
Bass: Neil Fairclough
Drums: Roger Taylor
```

5. Edit the `fleetwoodmac.txt` file, changing the lead singer from Stevie Nicks to Stevie Chicks (one of my chickens).  Save the file, but do not stage it.

```bash
senthilkumar.m@terminalgit-diff-exercise % vi fleetwoodmac.txt 
senthilkumar.m@terminalgit-diff-exercise % cat fleetwoodmac.txt 
Lead Vocals: Stevie Chicks
Lead Guitar: Mike Campbell
Bass: John McVie
Drums: Mick Fleetwood
Keyboard: Christine McVie
```

6. Run a diff that would reveal the unstaged changes in the working directory (you should see only the change to `fleetwoodmac.txt` printed out)

```bash
senthilkumar.m@terminalgit-diff-exercise % git diff
diff --git a/fleetwoodmac.txt b/fleetwoodmac.txt
index 653b184..9dae995 100644
--- a/fleetwoodmac.txt
+++ b/fleetwoodmac.txt
@@ -1,5 +1,5 @@
-Lead Vocals: Stevie Nicks
+Lead Vocals: Stevie Chicks
 Lead Guitar: Mike Campbell
 Bass: John McVie
 Drums: Mick Fleetwood
-Keyboard: Christine McVie
\ No newline at end of file
+Keyboard: Christine McVie
```

7. Run a diff that would reveal only the staged changes (you should only see the change to `queen.txt` printed out)

```bash
senthilkumar.m@terminalgit-diff-exercise % git diff --staged
diff --git a/queen.txt b/queen.txt
index 0e0fa0d..d698de5 100644
--- a/queen.txt
+++ b/queen.txt
@@ -1,4 +1,4 @@
-Lead Vocals: Adam Lambert
+Lead Vocals: Senthil Kumar
 Lead Guitar: Brian May
 Bass: Neil Fairclough
-Drums: Roger Taylor
\ No newline at end of file
+Drums: Roger Taylor
```

8. Run a diff that prints all changes (staged and unstaged) since the prior commit (you should see both changes printed out)

```bash
senthilkumar.m@terminalgit-diff-exercise % git diff HEAD
diff --git a/fleetwoodmac.txt b/fleetwoodmac.txt
index 653b184..9dae995 100644
--- a/fleetwoodmac.txt
+++ b/fleetwoodmac.txt
@@ -1,5 +1,5 @@
-Lead Vocals: Stevie Nicks
+Lead Vocals: Stevie Chicks
 Lead Guitar: Mike Campbell
 Bass: John McVie
 Drums: Mick Fleetwood
-Keyboard: Christine McVie
\ No newline at end of file
+Keyboard: Christine McVie
diff --git a/queen.txt b/queen.txt
index 0e0fa0d..d698de5 100644
--- a/queen.txt
+++ b/queen.txt
@@ -1,4 +1,4 @@
-Lead Vocals: Adam Lambert
+Lead Vocals: Senthil Kumar
 Lead Guitar: Brian May
 Bass: Neil Fairclough
-Drums: Roger Taylor
\ No newline at end of file
+Drums: Roger Taylor

```