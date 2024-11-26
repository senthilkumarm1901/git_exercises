## Commands executed after running the exercuse

- If you want to list all commits and when `Heads` or `tips` of branches move, you can use `git reflog`
 
```bash
% git reflog

093c19b HEAD@{0}: commit: add items needed to grow potatoes
0e6f2a2 HEAD@{1}: commit: add items needed for garden box
6259ece HEAD@{2}: commit: add ingredients for tomato soup
3c6f84b HEAD@{3}: commit (initial): create yard and groceries lists
```

- `git log` gives a detailed history of the commits made from the current branch

```bash
git log

commit 093c19bd27f187c2d34f254fa800a055c6a41ea4
Author: senthilkumarm1901 <senthilkumar.m1901@gmail.com>
Date:   Wed Nov 20 23:25:33 2024 +0530

    add items needed to grow potatoes

commit 0e6f2a2520dfe232de5e1576bb5f76b4e03089c7
Author: senthilkumarm1901 <senthilkumar.m1901@gmail.com>
Date:   Wed Nov 20 23:24:14 2024 +0530

    add items needed for garden box

commit 6259ece728fc0eac45f1f58c02db5fe8c8908526
Author: senthilkumarm1901 <senthilkumar.m1901@gmail.com>
Date:   Wed Nov 20 23:22:35 2024 +0530

    add ingredients for tomato soup

commit 3c6f84b998f94a9d58d596cf90e242daf8e71116
Author: senthilkumarm1901 <senthilkumar.m1901@gmail.com>
Date:   Wed Nov 20 23:21:34 2024 +0530

    create yard and groceries lists
```

- Most used git command - `git status`

```bash
git status

On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git_commands.md 

nothing added to commit but untracked files present (use "git add" to track)
```

- How after adding `git_commands.md` to `.gitignore` the file disappears from Untracked files in `git status`

```bash
echo "git_commands.md" >> .gitignore
git add .gitignore
git commit -m 'add gitignore file'
```

```bash
# git status
On branch main
nothing to commit, working tree clean
```