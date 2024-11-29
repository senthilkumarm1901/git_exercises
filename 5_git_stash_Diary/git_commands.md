# Stashing Exercise

## Part 1
1. Initialize a new git repo in a folder
2. Create a file called `diary.txt`.  Inside the file, add the following:
    
    ```
    I love my boss
    ```
    
3. Add and commit the changes on the `master` branch
4. Create a new branch called `the-truth`.  Switch to it.
5. In the `diary.txt` file, erase the contents and instead replace it with:
    
    ```
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    ```
    
6. Save the file


```bash
senthilkumar.m@terminal  sec9_git-stashing % mkdir -p Diary
senthilkumar.m@terminal  sec9_git-stashing % cd Diary 
senthilkumar.m@terminal  Diary % git init
Initialized empty Git repository in /Users/senthilkumar.m/Library/CloudStorage/OneDrive-TOYOTAConnectedIndia/Learnings/udemy_courses/git_udemy_course/sec9_git-stashing/Diary/.git/
senthilkumar.m@terminal  Diary % echo "I love my boss" >> diary.txt
senthilkumar.m@terminal  Diary % git add diary.txt && git commit -m "updated with first commit"
[main (root-commit) 00662c1] updated with first commit
 1 file changed, 1 insertion(+)
 create mode 100644 diary.txt
senthilkumar.m@terminal  Diary % git switch -c the-truth
Switched to a new branch 'the-truth'
senthilkumar.m@terminal  Diary % vi diary.txt 
senthilkumar.m@terminal  Diary % cat diary.txt 
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
```

---

## Part 2

7. **OH NO!** Your boss is walking towards you! Quick, switch over to the `master` branch!
8. **WHATTT?** The `diary.txt` file still contains our confession?  **Quick, stash the changes before your boss sees!!**
9. Your `diary.txt` file should now only contain "I love my boss"

```bash
senthilkumar.m@terminal  Diary % git switch main 
M	diary.txt
Switched to branch 'main'
senthilkumar.m@terminal  Diary % cat diary.txt 
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
senthilkumar.m@terminal  Diary % git stash
Saved working directory and index state WIP on main: 00662c1 updated with first commit
senthilkumar.m@terminal  Diary % cat diary.txt 
I love my boss
```

---

## Part 3

10. As your boss walks by, add more lies to the `diary.txt` file:
    
    ```
    I love my boss
    I love my boss
    I love my boss
    ```
    
11. Add and commit your changes on the `master` branch.

```bash
senthilkumar.m@terminal  Diary % vi diary.txt 
senthilkumar.m@terminal  Diary % cat diary.txt 
I love my boss
I love my boss
I love my boss
I love my boss
senthilkumar.m@terminal  git add diary.txt && git commit -m "updated with second commit in main"
[main 7b7f7e1] updated with second commit in main
 1 file changed, 3 insertions(+)
senthilkumar.m@terminal  Diary % git status
On branch main
nothing to commit, working tree clean
```

## Part 4

12. Now that your boss has left, it's safe to get back to the truth! Switch over to the `the-truth` branch.
13. Retrieve the earlier changes that you stashed (I HATE MY BOSS x 5)
14. Add and commit the changes on the `the-truth` branch

```bash
senthilkumar.m@terminal  Diary % git switch the-truth
Switched to branch 'the-truth'
senthilkumar.m@terminal  Diary % cat diary.txt 
I love my boss
senthilkumar.m@terminal  Diary % git stash pop
On branch the-truth
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   diary.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (41d6e87024ec0169505a3856e8b21cf41628bacf)
senthilkumar.m@terminal  Diary % cat diary.txt 
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
    I HATE MY BOSS
senthilkumar.m@terminal  Diary % git add diary.txt && git commit -m "final truth in the-truth branch"
[the-truth 6c12383] final truth in the-truth branch
 1 file changed, 5 insertions(+), 1 deletion(-)
senthilkumar.m@terminal  Diary % git status
On branch the-truth
nothing to commit, working tree clean
```