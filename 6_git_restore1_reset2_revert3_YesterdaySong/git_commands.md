# Undoing Things Exercise

This exercise is based around the Beatles' song Yesterday, and the evolution of its lyrics over time. 

- Clone the repo I've created for you, using the following command (make sure you're not already in a repo when you run it!)

```
git clone https://github.com/Colt/yesterday-exercise
```

## Part 1

- Change into the newly created directory.  You should see a file called `lyrics.txt`
- Take a look at the commit history.  You should see 8 commits on the master branch.

```bash
senthilkumar.m@terminal  sec10_undo-changes % cd yesterday-exercise 
senthilkumar.m@terminal  yesterday-exercise % git config user.email "senthilkumar.m1901@gmail.com"
senthilkumar.m@terminal  yesterday-exercise % git config user.name "senthilkumarm1901"
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
Oh, I believe in yesterday%     
```

## Part 2

- Go "back in time" by checking out the very first commit.  Remember, this puts you in detached HEAD.  Take a look at the `lyrics.txt` file to verify things have changed.  Then, leave detached HEAD by returning to the master branch.

```bash
senthilkumar.m@terminal  yesterday-exercise % git checkout 485a339
Note: switching to '485a339'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 485a339 add original first verse
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
Scrambled eggs
Have an omelette with some Muenster cheese
Put your dishes in the wash bin please
So I can clean the scrambled eggs
senthilkumar.m@terminal  yesterday-exercise % git switch master 
Previous HEAD position was 485a339 add original first verse
Switched to branch 'master'
Your branch is up to date with 'origin/master'.      
```

## Part 3

- Go back to the commit where the original version of the lyrics was completed.  The commit has the message "finish original lyrics".  Create a new branch called `scrambled-eggs` based upon this commit.

```bash
senthilkumar.m@terminal  yesterday-exercise % git checkout cdd927c
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
senthilkumar.m@terminal  yesterday-exercise % git switch -c scrambled-eggs
Switched to a new branch 'scrambled-eggs'
senthilkumar.m@terminal  yesterday-exercise % cat lyrics.txt 
Scrambled eggs
Have an omelette with some Muenster cheese
Put your dishes in the wash bin please
So I can clean the scrambled eggs

Join me do
There’s a lot of eggs for me and you
I’ve got ham and cheese and bacon too
So go get two and join me do

Fried or sunny side
Just aren’t right
The mix-bowl begs
Quick, go get a pan, and we’ll scramble up some eggs, eggs, eggs, eggs

Scrambled eggs
Good for breakfast, dinner time or brunch
Don’t buy six or twelve, buy a bunch
And we’ll have a lunch on scrambled eggs%  
```


## Part 4

- Go back to the `master` branch
- Delete everything in the `lyrics.txt` file.  Save the file.
- Oh no, that was a mistake!  USING A GIT COMMAND, discard the changes you made to `lyrics.txt` since the last commit. We saw a couple of ways of achieving this.

```bash
senthilkumar.m@terminal  yesterday-exercise % git switch master 
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
senthilkumar.m@terminal  yesterday-exercise % echo "" > lyrics.txt
senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   lyrics.txt

no changes added to commit (use "git add" and/or "git commit -a")
senthilkumar.m@terminal  yesterday-exercise % git restore lyrics.txt 
senthilkumar.m@terminal  yesterday-exercise % git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

```

## Part 5
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

## Part 6

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
Oh, I believe in yesterday%                                                                                                                                                        senthilkumar.m@terminal  yesterday-exercise % git status
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

## Part 7
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