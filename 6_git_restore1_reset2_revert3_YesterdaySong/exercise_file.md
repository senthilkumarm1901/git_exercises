# Undoing Things Exercise

This exercise is based around the Beatles' song Yesterday, and the evolution of its lyrics over time. 

- Clone the repo I've created for you, using the following command (make sure you're not already in a repo when you run it!)

```
git clone https://github.com/Colt/yesterday-exercise
```

- Change into the newly created directory.  You should see a file called `lyrics.txt`
- Take a look at the commit history.  You should see 8 commits on the master branch.
- Go "back in time" by checking out the very first commit.  Remember, this puts you in detached HEAD.  Take a look at the `lyrics.txt` file to verify things have changed.  Then, leave detached HEAD by returning to the master branch.
- Go back to the commit where the original version of the lyrics was completed.  The commit has the message "finish original lyrics".  Create a new branch called `scrambled-eggs` based upon this commit.
- Go back to the `master` branch
- Delete everything in the `lyrics.txt` file.  Save the file.
- Oh no, that was a mistake!  USING A GIT COMMAND, discard the changes you made to `lyrics.txt` since the last commit. We saw a couple of ways of achieving this.
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
- After more consideration, you realize that you actually don't want the previous two commits (the 404 parody lyrics) on the master branch.  You want to move them to a new branch!
- Use a git command to "undo" the prior two commits on master.  Make sure you **KEEP THE CHANGES IN YOUR WORKING DIRECTORY.**  Just undo the two git commits.  Your `lyrics.txt` file should still contain the 404 lyrics.
- Create a new branch called 404, switch to it, and add and commit the 404 lyrics in your working directory.
- Switch back to master and make sure `lyrics.txt` contains the actual lyrics to Yesterday
