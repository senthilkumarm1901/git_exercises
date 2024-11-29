# Undoing Things Exercise
## ***********PART 1**************


This exercise is based around the Beatles' song Yesterday, and the evolution of its lyrics over time. 

- Clone the repo I've created for you, using the following command (make sure you're not already in a repo when you run it!)

```bash
git clone https://github.com/Colt/yesterday-exercise
```

---

## ***********PART 2**************
- Change into the newly created directory.  You should see a file called `lyrics.txt`
- Take a look at the commit history.  You should see 8 commits on the master branch.

```bash
senthilkumar.m@terminal  yesterday-exercise % git log --oneline --all  | nl
     1	f199959 rework final verse
     2	8e3111c rework chorus
     3	b88b254 rework second verse
     4	b593444 rework first verse
     5	cdd927c finish original lyrics
     6	9518e20 add original chorus
     7	9858f43 add original second verse
     8	485a339 add original first verse
```

---

## ***********PART 3**************
- Go "back in time" by checking out the very first commit.  Remember, this puts you in detached HEAD.  Take a look at the `lyrics.txt` file to verify things have changed.  Then, leave detached HEAD by returning to the master branch.

```bash
senthilkumar.m@terminal  yesterday-exercise % git checkout 485a339 && echo -n "\nLooking at the file:\n" && cat lyrics.txt 
HEAD is now at 485a339 add original first verse

Looking at the file:
Scrambled eggs
Have an omelette with some Muenster cheese
Put your dishes in the wash bin please
So I can clean the scrambled eggs
senthilkumar.m@terminal  yesterday-exercise % git switch master
Previous HEAD position was 485a339 add original first verse
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
```

---

## ***********PART 4**************
- Go back to the commit where the original version of the lyrics was completed.  The commit has the message "finish original lyrics".  Create a new branch called `scrambled-eggs` based upon this commit.


```bash
senthilkumar.m@terminal  yesterday-exercise % git checkout cdd927c  && git switch -c scrambled-eggs
Note: switching to 'cdd927c'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at cdd927c finish original lyrics
Switched to a new branch 'scrambled-eggs'
senthilkumar.m@terminal  yesterday-exercise % git log --oneline --decorate --all
f199959 (origin/master, origin/HEAD, master) rework final verse
8e3111c rework chorus
b88b254 rework second verse
b593444 rework first verse
cdd927c (HEAD -> scrambled-eggs) finish original lyrics
9518e20 add original chorus
9858f43 add original second verse
485a339 add original first verse
```
---

## ***********PART 5**************
- Go back to the `master` branch
- Delete everything in the `lyrics.txt` file.  Save the file.
- Oh no, that was a mistake!  USING A GIT COMMAND, discard the changes you made to `lyrics.txt` since the last commit. We saw a couple of ways of achieving this.


```bash
senthilkumar.m@terminal  yesterday-exercise % git switch master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
senthilkumar.m@terminal  yesterday-exercise % echo "" > lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % git restore lyrics.txt 
# you can also use `git checkout HEAD lyrics.txt`
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
Yesterday
All my troubles seemed so far away
Now it looks as though they're here to stay
Oh, I believe in yesterday

Suddenly
I'm not half the man I used to be
There's a shadow hanging over me
Oh, yesterday came suddenly

Why she had to go
I don't know, she wouldn't say
I said something wrong
Now I long for yesterday

Yesterday
Love was such an easy game to play
Now I need a place to hide away
Oh, I believe in yesterday  
```
---

## ***********PART 6**************
- Suddenly you get a creative itch! You want to write your own parody lyrics!  Replace the contents of `lyrics.txt` with the following lyrics (from [this website](http://www.amiright.com/parody/60s/thebeatles1981.shtml))
    
    ```
    404
    Guess this ain't the page you're looking for
    On this website there are thousands more
    With no error 404
    
    Suddenly
    This is not the page you thought you'd see
    But it's not an error 403
    Yes, 404s come easily
    ```
    
- Add and commit the changes on the `master` branch
- Add this to the bottom of the `lyrics.txt` file:
    
    ```
    Why it has to show, I don't know
    Or what it's for
    You typed something wrong?
    Here's no song - it's 404
    
    404
    Adding 1% to twenty score
    (I put that line in 'cause it scans, no more)
    "Goodbye" from error 404
    ```
    
- Add and commit the changes to the `master` branch


```bash
senthilkumar.m@terminal  yesterday-exercise % echo "" > lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % vi lyrics.txt 
senthilkumar.m@terminal  yesterday-exercise % git add lyrics.txt && git commit -m "first parody commit added"
[master 1179b1e] first parody commit added
 1 file changed, 9 insertions(+), 19 deletions(-)
senthilkumar.m@terminal  yesterday-exercise % vi lyrics.txt 
senthilkumar.m@terminal  yesterday-exercise % git add lyrics.txt && git commit -m "second parody commit added"
[master 04f3962] second parody commit added
 1 file changed, 10 insertions(+)
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
    404
    Guess this ain't the page you're looking for
    On this website there are thousands more
    With no error 404
    
    Suddenly
    This is not the page you thought you'd see
    But it's not an error 403
    Yes, 404s come easily

    Why it has to show, I don't know
    Or what it's for
    You typed something wrong?
    Here's no song - it's 404
    
    404
    Adding 1% to twenty score
    (I put that line in 'cause it scans, no more)
    "Goodbye" from error 404
```

# Attempt 1 - Using `git restore` in Part 7 and 8
## ***********PART 7**************


- After more consideration, you realize that you actually don't want the previous two commits (the 404 parody lyrics) on the master branch.  You want to move them to a new branch!
- Use a git command to "undo" the prior two commits on master.  Make sure you **KEEP THE CHANGES IN YOUR WORKING DIRECTORY.**  Just undo the two git commits.  Your `lyrics.txt` file should still contain the 404 lyrics.

```bash
senthilkumar.m@terminal  yesterday-exercise % git log --oneline --all
ebb7132 (HEAD -> master) second parody lyrics commit
6de3bd3 first parody lyrics commit
f199959 (origin/master, origin/HEAD) rework final verse
8e3111c rework chorus
b88b254 rework second verse
b593444 rework first verse
cdd927c (scrambled-eggs) finish original lyrics
9518e20 add original chorus
9858f43 add original second verse
485a339 add original first verse
senthilkumar.m@terminal  yesterday-exercise % git restore --source f199959 lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
Yesterday
All my troubles seemed so far away
Now it looks as though they're here to stay
Oh, I believe in yesterday

Suddenly
I'm not half the man I used to be
There's a shadow hanging over me
Oh, yesterday came suddenly

Why she had to go
I don't know, she wouldn't say
I said something wrong
Now I long for yesterday

Yesterday
Love was such an easy game to play
Now I need a place to hide away
Oh, I believe in yesterday                                                                                senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   lyrics.txt

no changes added to commit (use "git add" and/or "git commit -a")
senthilkumar.m@terminal  yesterday-exercise % git add lyrics.txt && git commit -m "restored the lyrics to original YesterdaySong"
[master 37e205c] restored the lyrics to original YesterdaySong
 1 file changed, 18 insertions(+), 18 deletions(-)
```

---


## ***********PART 8**************
- Create a new branch called 404, switch to it, and add and commit the 404 lyrics in your working directory.
- Switch back to master and make sure `lyrics.txt` contains the actual lyrics to Yesterday


```bash
senthilkumar.m@terminal  yesterday-exercise % git restore --source ebb7132 lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % git status
On branch 404
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   lyrics.txt

no changes added to commit (use "git add" and/or "git commit -a")
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
    404
    Guess this ain't the page you're looking for
    On this website there are thousands more
    With no error 404
    
    Suddenly
    This is not the page you thought you'd see
    But it's not an error 403
    Yes, 404s come easily

    Why it has to show, I don't know
    Or what it's for
    You typed something wrong?
    Here's no song - it's 404
    
    404
    Adding 1% to twenty score
    (I put that line in 'cause it scans, no more)
    "Goodbye" from error 404
senthilkumar.m@terminal  yesterday-exercise % git add lyrics.txt && git commit -m "this 404 branch has 404 lyrics"
[404 af249ab] this 404 branch has 404 lyrics
 1 file changed, 18 insertions(+), 18 deletions(-)

```



```bash
senthilkumar.m@terminal  yesterday-exercise % git log --oneline --all
af249ab (HEAD -> 404) this 404 branch has 404 lyrics
37e205c (master) restored the lyrics to original YesterdaySong
ebb7132 second parody lyrics commit
6de3bd3 first parody lyrics commit
f199959 (origin/master, origin/HEAD) rework final verse
8e3111c rework chorus
b88b254 rework second verse
b593444 rework first verse
cdd927c (scrambled-eggs) finish original lyrics
9518e20 add original chorus
9858f43 add original second verse
485a339 add original first verse

af249ab (HEAD -> 404) refs/heads/404@{0}: commit: this 404 branch has 404 lyrics
af249ab (HEAD -> 404) HEAD@{0}: commit: this 404 branch has 404 lyrics
37e205c (master) refs/heads/404@{1}: branch: Created from HEAD
37e205c (master) HEAD@{1}: checkout: moving from master to 404
37e205c (master) refs/heads/master@{0}: commit: restored the lyrics to original YesterdaySong
37e205c (master) HEAD@{2}: commit: restored the lyrics to original YesterdaySong
ebb7132 refs/heads/master@{1}: commit: second parody lyrics commit
ebb7132 HEAD@{3}: commit: second parody lyrics commit
6de3bd3 refs/heads/master@{2}: commit: first parody lyrics commit
6de3bd3 HEAD@{4}: commit: first parody lyrics commit
f199959 (origin/master, origin/HEAD) HEAD@{5}: checkout: moving from scrambled-eggs to master
cdd927c (scrambled-eggs) refs/heads/scrambled-eggs@{0}: branch: Created from HEAD
cdd927c (scrambled-eggs) HEAD@{6}: checkout: moving from cdd927c0bebbef64adf38f8cb58a186d33aaeeab to scrambled-eggs
cdd927c (scrambled-eggs) HEAD@{7}: checkout: moving from master to cdd927c
f199959 (origin/master, origin/HEAD) HEAD@{8}: checkout: moving from 485a33962fc19a957cabb54273e99465fdba9c9d to master
485a339 HEAD@{9}: checkout: moving from master to 485a339
f199959 (origin/master, origin/HEAD) refs/heads/master@{3}: clone: from https://github.com/Colt/yesterday-exercise
f199959 (origin/master, origin/HEAD) refs/remotes/origin/HEAD@{0}: clone: from https://github.com/Colt/yesterday-exercise
f199959 (origin/master, origin/HEAD) HEAD@{10}: clone: from https://github.com/Colt/yesterday-exercise
```

---

# Attempt 2 - Using `git reset` in Part 7 and 8

## ***********PART 7**************
- After more consideration, you realize that you actually don't want the previous two commits (the 404 parody lyrics) on the master branch.  You want to move them to a new branch!
- Use a git command to "undo" the prior two commits on master.  Make sure you **KEEP THE CHANGES IN YOUR WORKING DIRECTORY.**  Just undo the two git commits.  Your `lyrics.txt` file should still contain the 404 lyrics.

```bash
senthilkumar.m@terminal  yesterday-exercise % git reset --soft HEAD~2
senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   lyrics.txt

senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
    404
    Guess this ain't the page you're looking for
    On this website there are thousands more
    With no error 404
    
    Suddenly
    This is not the page you thought you'd see
    But it's not an error 403
    Yes, 404s come easily

    Why it has to show, I don't know
    Or what it's for
    You typed something wrong?
    Here's no song - it's 404
    
    404
    Adding 1% to twenty score
    (I put that line in 'cause it scans, no more)
    "Goodbye" from error 404
```

## ***********PART 8**************
- Create a new branch called 404, switch to it, and add and commit the 404 lyrics in your working directory.
- Switch back to master and make sure `lyrics.txt` contains the actual lyrics to Yesterday

```bash
senthilkumar.m@terminal  yesterday-exercise % git stash   
Saved working directory and index state WIP on master: f199959 rework final verse
senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
senthilkumar.m@terminal  yesterday-exercise % git switch -c 404
Switched to a new branch '404'
senthilkumar.m@terminal  yesterday-exercise % git stash pop
On branch 404
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   lyrics.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (ac835132aafe3b18b9b8b288eab0d63f6dd10bec)
senthilkumar.m@terminal  yesterday-exercise % git add lyrics.txt && git commit -m "add 404 lyrics in 404 branch"
[404 4152b4e] add 404 lyrics in 404 branch
 1 file changed, 18 insertions(+), 18 deletions(-)
senthilkumar.m@terminal  yesterday-exercise % git status
On branch 404
nothing to commit, working tree clean
```

- Note that the logs does not have the `parody` commits - `1179b1e` and `04f3962` -  at all now
- It is visible only in `git reflog`

```bash
senthilkumar.m@terminal  yesterday-exercise % git log --oneline --all
4152b4e (HEAD -> 404) add 404 lyrics in 404 branch
f199959 (origin/master, origin/HEAD, master) rework final verse
8e3111c rework chorus
b88b254 rework second verse
b593444 rework first verse
cdd927c (scrambled-eggs) finish original lyrics
9518e20 add original chorus
9858f43 add original second verse
485a339 add original first verse
senthilkumar.m@terminal  yesterday-exercise % git reflog --oneline --all
4152b4e (HEAD -> 404) refs/heads/404@{0}: commit: add 404 lyrics in 404 branch
4152b4e (HEAD -> 404) HEAD@{0}: commit: add 404 lyrics in 404 branch
f199959 (origin/master, origin/HEAD, master) refs/heads/404@{1}: branch: Created from HEAD
f199959 (origin/master, origin/HEAD, master) HEAD@{1}: checkout: moving from master to 404
f199959 (origin/master, origin/HEAD, master) HEAD@{2}: reset: moving to HEAD
f199959 (origin/master, origin/HEAD, master) refs/heads/master@{0}: reset: moving to HEAD~2
f199959 (origin/master, origin/HEAD, master) HEAD@{3}: reset: moving to HEAD~2
04f3962 HEAD@{4}: reset: moving to 04f39628410eaea4317051e2d81fbb00eeab34ac
04f3962 refs/heads/master@{1}: commit: second parody commit added
04f3962 HEAD@{5}: commit: second parody commit added
1179b1e refs/heads/master@{2}: commit: first parody commit added
1179b1e HEAD@{6}: commit: first parody commit added
f199959 (origin/master, origin/HEAD, master) HEAD@{7}: checkout: moving from scrambled-eggs to master
cdd927c (scrambled-eggs) refs/heads/scrambled-eggs@{0}: branch: Created from HEAD
cdd927c (scrambled-eggs) HEAD@{8}: checkout: moving from cdd927c0bebbef64adf38f8cb58a186d33aaeeab to scrambled-eggs
cdd927c (scrambled-eggs) HEAD@{9}: checkout: moving from master to cdd927c
f199959 (origin/master, origin/HEAD, master) HEAD@{10}: checkout: moving from 485a33962fc19a957cabb54273e99465fdba9c9d to master
485a339 HEAD@{11}: checkout: moving from master to 485a339
f199959 (origin/master, origin/HEAD, master) refs/heads/master@{3}: clone: from https://github.com/Colt/yesterday-exercise
f199959 (origin/master, origin/HEAD, master) refs/remotes/origin/HEAD@{0}: clone: from https://github.com/Colt/yesterday-exercise
f199959 (origin/master, origin/HEAD, master) HEAD@{12}: clone: from https://github.com/Colt/yesterday-exercise
```


# Attempt 3 - Using `git revert` in Part 7 and 8

## ***********PART 7**************


- After more consideration, you realize that you actually don't want the previous two commits (the 404 parody lyrics) on the master branch.  You want to move them to a new branch!
- Use a git command to "undo" the prior two commits on master.  Make sure you **KEEP THE CHANGES IN YOUR WORKING DIRECTORY.**  Just undo the two git commits.  Your `lyrics.txt` file should still contain the 404 lyrics.

```bash
senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
senthilkumar.m@terminal  yesterday-exercise % git log --oneline --all
82d049a (HEAD -> master) second parody commit added
9527d08 first parody commit added
f199959 (origin/master, origin/HEAD) rework final verse
8e3111c rework chorus
b88b254 rework second verse
b593444 rework first verse
cdd927c (scrambled-eggs) finish original lyrics
9518e20 add original chorus
9858f43 add original second verse
485a339 add original first verse
senthilkumar.m@terminal  yesterday-exercise % git revert f199959
Auto-merging lyrics.txt
CONFLICT (content): Merge conflict in lyrics.txt
error: could not revert f199959... rework final verse
hint: After resolving the conflicts, mark them with
hint: "git add/rm <pathspec>", then run
hint: "git revert --continue".
hint: You can instead skip this commit with "git revert --skip".
hint: To abort and get back to the state before "git revert",
hint: run "git revert --abort".
senthilkumar.m@terminal  yesterday-exercise % vi lyrics.txt 
senthilkumar.m@terminal  yesterday-exercise % vi lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % git diff f199959 82d049a
diff --git a/lyrics.txt b/lyrics.txt
index 519d824..bd8c72c 100644
--- a/lyrics.txt
+++ b/lyrics.txt
@@ -1,19 +1,19 @@
-Yesterday
-All my troubles seemed so far away
-Now it looks as though they're here to stay
-Oh, I believe in yesterday
+    404
+    Guess this ain't the page you're looking for
+    On this website there are thousands more
+    With no error 404
+    
+    Suddenly
+    This is not the page you thought you'd see
+    But it's not an error 403
+    Yes, 404s come easily
 
-Suddenly
-I'm not half the man I used to be
-There's a shadow hanging over me
-Oh, yesterday came suddenly
-
-Why she had to go
-I don't know, she wouldn't say
-I said something wrong
-Now I long for yesterday
-
-Yesterday
-Love was such an easy game to play
-Now I need a place to hide away
-Oh, I believe in yesterday
\ No newline at end of file
+    Why it has to show, I don't know
+    Or what it's for
+    You typed something wrong?
+    Here's no song - it's 404
+    
+    404
+    Adding 1% to twenty score
+    (I put that line in 'cause it scans, no more)
+    "Goodbye" from error 404

senthilkumar.m@terminal  yesterday-exercise % git show f199959:lyrics.txt 
Yesterday
All my troubles seemed so far away
Now it looks as though they're here to stay
Oh, I believe in yesterday

Suddenly
I'm not half the man I used to be
There's a shadow hanging over me
Oh, yesterday came suddenly

Why she had to go
I don't know, she wouldn't say
I said something wrong
Now I long for yesterday

Yesterday
Love was such an easy game to play
Now I need a place to hide away
Oh, I believe in yesterday

senthilkumar.m@terminal  yesterday-exercise % git show 82d049a:lyrics.txt
    404
    Guess this ain't the page you're looking for
    On this website there are thousands more
    With no error 404
    
    Suddenly
    This is not the page you thought you'd see
    But it's not an error 403
    Yes, 404s come easily

    Why it has to show, I don't know
    Or what it's for
    You typed something wrong?
    Here's no song - it's 404
    
    404
    Adding 1% to twenty score
    (I put that line in 'cause it scans, no more)
    "Goodbye" from error 404

senthilkumar.m@terminal  yesterday-exercise % vi lyrics.txt 
senthilkumar.m@terminal  yesterday-exercise % vi lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)

You are currently reverting commit f199959.
  (fix conflicts and run "git revert --continue")
  (use "git revert --skip" to skip this patch)
  (use "git revert --abort" to cancel the revert operation)

Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
	both modified:   lyrics.txt

no changes added to commit (use "git add" and/or "git commit -a")
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt     
Yesterday
All my troubles seemed so far away
Now it looks as though they're here to stay
Oh, I believe in yesterday

Suddenly
I'm not half the man I used to be
There's a shadow hanging over me
Oh, yesterday came suddenly

Why she had to go
I don't know, she wouldn't say
I said something wrong
Now I long for yesterday

Scrambled eggs
Good for breakfast, dinner time or brunch
Don’t buy six or twelve, buy a bunch
And we’ll have a lunch on scrambled eggs

senthilkumar.m@terminal  yesterday-exercise % git add lyrics.txt && git commit -m "restored to original YesterdaySong lyrics"
[master 55d3c06] restored to original YesterdaySong lyrics
 1 file changed, 18 insertions(+), 18 deletions(-)

senthilkumar.m@terminal  yesterday-exercise % git log --oneline --all
55d3c06 (HEAD -> master) restored to original YesterdaySong lyrics
82d049a second parody commit added
9527d08 first parody commit added
f199959 (origin/master, origin/HEAD) rework final verse
8e3111c rework chorus
b88b254 rework second verse
b593444 rework first verse
cdd927c (scrambled-eggs) finish original lyrics
9518e20 add original chorus
9858f43 add original second verse
485a339 add original first verse
```

