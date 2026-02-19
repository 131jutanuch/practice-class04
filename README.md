# INT142 Software Development Tools

## Class 04 Resolve Conflicts in VCS

### Overview

In this class, you will create a new branch `class04` and work on this branch instead of `main`. `index.html` will be pulled from `IT-BANGMOD-INT142-2025/class02-<your-github-id>` repository. GitHub Action is used to create a new commit on remote repository to simulate having a collaborator pushing a new commit ahead of your local commit. You need to resolve conflicts correctly before you can push your work to remote repository.

---

### Stage 1 - Create `class04` branch and add `index.html` from `class02` to `class04` repository

### Instructions

1. Clone `class04-<your-github-id>` repository to `Documents/<your-github-id>/class04`

2. Configure author's name and author's email to `<Firstname Surname> (INT142-class04)` and `<your-private-github-email>`, respectively

3. Create a new branch `class04`

4. Switch to `class04` branch.

5. Pull files from `IT-BANGMOD-INT142-2025/class02-<your-github-id>` without making a commit and commit histories

   ```bash
   remote: Enumerating objects: 17, done.
   remote: Counting objects: 100% (8/8), done.
   remote: Compressing objects: 100% (4/4), done.
   remote: Total 17 (delta 4), reused 6 (delta 4), pack-reused 9 (from 1)
   Unpacking objects: 100% (17/17), 7.47 KiB | 103.00 KiB/s, done.
   From https://github.com/IT-BANGMOD-INT142-2025/class02-olarnr-ad-sit
   * branch            main       -> FETCH_HEAD
   Auto-merging .github/workflows/classroom.yml
   CONFLICT (add/add): Merge conflict in .github/workflows/classroom.yml
   Auto-merging README.md
   CONFLICT (add/add): Merge conflict in README.md
   Squash commit -- not updating HEAD
   Automatic merge failed; fix conflicts and then commit the result.
   ```

6. Fix the conflict using VS Code
   - Keep `README.md` and `classroom.yml` from this repository (class04)
   - Do not modify `index.html`
   - Add both files to staging area (index)

   If you fix conflicts correctly, the output from `git status` must show as follows:

   ```bash
   $ git add .
   $ git status
   On branch class04
   Changes to be committed:
   (use "git restore --staged <file>..." to unstage)
           new file:   index.html
   ```

7. Commit your work with the message `Add index.html from class02`. Check commit history and make sure that it is correct. If not, amend the commit meta-data.

8. Push your local commit in `class04` branch to `remotes/origin/class04`

9. Check Test 3 on GitHub, you must pass Test 3 before proceeding to Stage 2
   ```
   Test runner summary
   ┌────────────────────┬─────────────┬─────────────┐
   │ Test Runner Name   │ Test Score  │ Max Score   │
   ├────────────────────┼─────────────┼─────────────┤
   │ test-1             │ 10          │ 10          │
   ├────────────────────┼─────────────┼─────────────┤
   │ test-2             │ 10          │ 10          │
   ├────────────────────┼─────────────┼─────────────┤
   │ test-3             │ 30          │ 30          │
   ├────────────────────┼─────────────┼─────────────┤
   │ test-4             │ 0           │ 10          │
   ├────────────────────┼─────────────┼─────────────┤
   │ test-5             │ 0           │ 30          │
   ├────────────────────┼─────────────┼─────────────┤
   │ Total:             │ 50          │ 90          │
   └────────────────────┴─────────────┴─────────────┘
   ```

---

### Stage 2 - Update `index.html` on `class04` branch

### Instructions

0.  **DO NOT PULL NEW COMMIT FROM REMOTE REPOSITORY**  
    If you made a mistake, you will have to restart by deleting `class04` branch on both local and remote repository, and start again.

    BE MINDFUL OF WHAT YOU ARE DOING!

    ```bash
    $ git switch main
    $ git branch -D class04        # force deletion local branch
    $ git push origin -d class04   # delete class04 on origin
    ```

1.  Modify `index.html`. Replace the sentence  
    `This page was created locally and pushed to GitHub Classroom.` with  
    `This page was pulled from class02 repository.`.
    ```bash
    $ git diff
    diff --git a/index.html b/index.html
    index 8703068..1cde087 100644
    --- a/index.html
    +++ b/index.html
    @@ -16,7 +16,7 @@
    <h1 id="class">Class 02 Exercise 2</h1>
    <h2 id="student-name">Olarn Rojanapornpun</h2>

        -        <p>This page was created locally and pushed to GitHub Classroom.</p>
        +        <p>This page was pulled from class02 repository.</p>
            </div>

        </body>
        ```

2.  Commit your change with the message `Update index.html line 19`

3.  Push the new commit to remote repository.

    ```bash
     ! [rejected]        class04 -> class04 (fetch first)
    error: failed to push some refs to 'github-olarn-ad:INT142-2025-SPIKES/class04-olarnr-ad-sit.git'
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    ```

4.  Use `git fetch` to see the commits on remote repository. Use `git status` to see the status of your local repository.

5.  Use `git pull` to merge your local commit with the latest commit on remote repository.

6.  Accept changes from `incoming`. Keep your name and the change you have made in step 1.

    After the fix, the `git diff` result is as follows.

    ```bash
    $ git diff index.html
    diff --cc index.html
    index 1cde087,a964190..0000000
    --- a/index.html
    +++ b/index.html
    @@@ -13,10 -13,11 +13,10 @@@

        <div class="container">
            <h1>INT142 Software Development Tools</h1>
    -         <h1 id="class">Class 02 Exercise 2</h1>
    +         <h1 id="class">Class 04</h1>
    -        <h2 id="student-name">Replace This With Your Name</h2>
    +        <h2 id="student-name">Olarn Rojanapornpun</h2>

    -        <p>This page was modified by GitHub Actions.</p>
    -
    +        <p>This page was pulled from class02 repository.</p>
        </div>

    </body>
    ```

    ```bash
    $ git diff --cached
    diff --git a/index.html b/index.html
    index 1cde087..87966d1 100644
    --- a/index.html
    +++ b/index.html
    @@ -3,7 +3,7 @@
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    -    <title>Class 02 Exercise 2</title>
    +    <title>Class 04</title>
        <style>
            body { font-family: sans-serif; text-align: center; margin-top: 50px; }
            .container { border: 1px solid #ccc; padding: 20px; border-radius: 8px; max-width: 600px; margin: 0 auto; }
    @@ -13,7 +13,7 @@

        <div class="container">
            <h1>INT142 Software Development Tools</h1>
    -        <h1 id="class">Class 02 Exercise 2</h1>
    +        <h1 id="class">Class 04</h1>
            <h2 id="student-name">Olarn Rojanapornpun</h2>

            <p>This page was pulled from class02 repository.</p>
    ```

7.  Follow instructions in `git status` to complete the merge commit (with the default merge message) and push this merge commit to remote repository.

8.  In the initial version of this assignment, the full score is 80 since there is a problem with Test 1 script.
    `     Test runner summary
    ┌────────────────────┬─────────────┬─────────────┐
    │ Test Runner Name   │ Test Score  │ Max Score   │
    ├────────────────────┼─────────────┼─────────────┤
    │ test-1             │ 10          │ 10          │
    ├────────────────────┼─────────────┼─────────────┤
    │ test-2             │ 10          │ 10          │
    ├────────────────────┼─────────────┼─────────────┤
    │ test-3             │ 30          │ 30          │
    ├────────────────────┼─────────────┼─────────────┤
    │ test-4             │ 10          │ 10          │
    ├────────────────────┼─────────────┼─────────────┤
    │ test-5             │ 30          │ 30          │
    ├────────────────────┼─────────────┼─────────────┤
    │ Total:             │ 90          │ 90          │
    └────────────────────┴─────────────┴─────────────┘
    `
    [![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/3ACHtEIJ)

# INT142 Software Development Tools

## Class 02 Working on local repository first

### Exercise 1

In this class exercise, you will initialize empty git repository on your local machine first. After working on your class02 exercise 1 work, you will push your work to **empty** remote repository on **your github account**.

### Instructions

1. Move to your class directory

   ```bash
   $ cd Documents/<your-github-id>
   ```

2. Create a new directory for this exercise

   ```bash
   $ mkdir class02-ex1
   ```

3. Move to this exercise directory

   ```bash
   $ cd class02-ex1
   ```

4. Initialize empty repository and check that it is initialized

   ```bash
   $ git init

   $ git status
   ```

5. Open VS Code

   ```bash
   $ code .
   ```

6. Create a new file `index.html` and copy the following html code and save the file.

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       <title>Class 02 Exercise 1</title>
       <style>
         body {
           font-family: sans-serif;
           text-align: center;
           margin-top: 50px;
         }
         .container {
           border: 1px solid #ccc;
           padding: 20px;
           border-radius: 8px;
           max-width: 600px;
           margin: 0 auto;
         }
       </style>
     </head>
     <body>
       <div class="container">
         <h1>INT142 Software Development Tools</h1>
         <h1 id="class">Class 02 Exercise 1</h1>
         <h2 id="student-name">Replace This With Your Name</h2>

         <p>This page was created locally and pushed to GitHub Classroom.</p>
       </div>
     </body>
   </html>
   ```

7. Add `index.html` to the staging area

   ```bash
   $ git add .
   ```

8. Commit your work

   ```bash
   $ git commit -m "Initial commit - add index.html"
   ```

9. View commit history

   ```bash
   $ git log
   ```

10. Change commit author name and email as follows:

    ```bash
    $ git config --local user.name "<Firstname Surname> (INT142-class02)"

    $ git config --local user.email <your-private-github-email>
    ```

    Amend previous commit without changing the commit message:

    ```bash
    $ git commit --amend --reset-author --no-edit
    ```

    Amend the commit message:

    ```bash
    $ git commit --amend -m "<new message>"
    ```

    Ensure that your commit author and message are correct before proceeding to the next step.

11. Rename default branch to `main` (needed on Windows only)

    ```bash
    $ git branch -M main
    ```

12. Create new repository on your personal GitHub account with the name `INT142-class02`. Set it to `private`.

13. Add remote repository

    ```bash
    $ git remote add origin https://github.com/<your-github-username>/INT142-class02.git
    ```

14. View remote setting

    ```bash
    $ git remote -v
    ```

    Ensure that the url is correct. If not, use the following command to set url.

    ```bash
    $ git remote set-url origin <new-url>
    ```

15. Make sure that the remote url is correct by fetching from remote repository

    ```bash
    $ git fetch
    ```

16. Check the current local repository status.

    ```bash
    $ git status
    On branch main
    nothing to commit, working tree clean
    ```

17. Push your work to the remote repository

    ```bash
    $ git push -u origin main
    ```

    You should have successfully push `index.html` to your GitHub repository.

18. Update `index.html`, replace `Replace This With Your Name` with your fullname.

19. Add the updated `index.html` to the staging area and commit with the message `Update index.html with student name`

20. Push the update to your remote repository

---

### Exercise 2

In this class exercise, you will start working on your local repository first as in Exercise 1. However, you will link this to GitHub classroom repository which is **not empty**.

### Instructions

1. Work on a new directory called `class02-ex2` under `Documents/<your-github-id>`

2. Create a new file `index.html` and copy the following html code and save the file.

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       <title>Class 02 Exercise 2</title>
       <style>
         body {
           font-family: sans-serif;
           text-align: center;
           margin-top: 50px;
         }
         .container {
           border: 1px solid #ccc;
           padding: 20px;
           border-radius: 8px;
           max-width: 600px;
           margin: 0 auto;
         }
       </style>
     </head>
     <body>
       <div class="container">
         <h1>INT142 Software Development Tools</h1>
         <h1 id="class">Class 02 Exercise 2</h1>
         <h2 id="student-name">Replace This With Your Name</h2>

         <p>This page was created locally and pushed to GitHub Classroom.</p>
       </div>
     </body>
   </html>
   ```

3. Initialize local repository

4. Configure `user.name` and `user.email` as in Exercise 1. Check that it is correct.

5. Rename default branch to `main` (needed on Windows only)

6. Add `index.html` to the staging area

7. Commit your work. Check commit history and make sure that it is correct. If not, amend the commit meta-data.

8. Add remote repository `https://github.com/IT-BANGMOD-INT142-2025/class02-<your-github-username>.git`. Check that the configuration is correct.

9. (Not normally needed) Manually configure upstream.

   ```bash
   $ git branch --set-upstream-to=origin/main main
   branch 'main' set up to track 'origin/main'.

   $ git branch -vv
   * main b54bb45 [origin/main: ahead 1, behind 2] Initial commit - add index.html
   ```

10. Fetch meta-data from the remote repository

    ```bash
    $ git fetch
    remote: Enumerating objects: 10, done.
    remote: Counting objects: 100% (10/10), done.
    remote: Compressing objects: 100% (4/4), done.
    Unpacking objects: 100% (10/10), 3.54 KiB | 725.00 KiB/s, done.
    remote: Total 10 (delta 1), reused 3 (delta 0), pack-reused 0 (from 0)
    From github-olarn-ad:IT-BANGMOD-INT142-2025/class02-olarnr-ad-sit
    * [new branch]      main       -> origin/main
    ```

11. Check the current local repository status.

    ```bash
    $ git status
    On branch main
    Your branch and 'origin/main' have diverged,
    and have 1 and 2 different commits each, respectively.
        (use "git pull" to merge the remote branch into yours)

    nothing to commit, working tree clean
    ```

12. Push your work to the remote repository. Since there is a commit on remote repository and local and remote repository have diverged, there will be error.

    ```bash
    $ git push -u origin main
     ! [rejected]        main -> main (non-fast-forward)
    error: failed to push some refs to 'github-olarn-ad:IT-BANGMOD-INT142-2025/class02-olarnr-ad-sit.git'
    hint: Updates were rejected because the tip of your current branch is behind
    hint: its remote counterpart. Integrate the remote changes (e.g.
    hint: 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    ```

13. You need merge commit on remote repository to your local repository before you can push your work to the remote repository.

    ```bash
    $ git pull origin main --allow-unrelated-histories --no-rebase --no-edit
    From github-olarn-ad:IT-BANGMOD-INT142-2025/class02-olarnr-ad-sit
    * branch            main       -> FETCH_HEAD
    Merge made by the 'ort' strategy.
    .github/workflows/classroom.yml | 135 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    1 file changed, 135 insertions(+)
    create mode 100644 .github/workflows/classroom.yml
    ```

    `--allow-unrelated-histories` since the two commits do not have common ancestor, needed this to merge  
    `--no-rebase` use merge, not rebase  
    `--no-edit` use auto-generated merge message

14. View commit history

    ```bash
    $ git log

    $ git log --graph --oneline
    *   bd45a16 (HEAD -> main) Merge branch 'main' of github-olarn-ad:IT-BANGMOD-INT142-2025/class02-olarnr-ad-sit
    |\
    | * 68f56e2 (origin/main) Initial commit
    * b54bb45 Initial commit - add index.html
    ```

15. Push to remote repository again

    ```bash
    $ git push
    Enumerating objects: 6, done.
    Counting objects: 100% (6/6), done.
    Delta compression using up to 10 threads
    Compressing objects: 100% (4/4), done.
    Writing objects: 100% (5/5), 986 bytes | 986.00 KiB/s, done.
    Total 5 (delta 1), reused 0 (delta 0), pack-reused 0
    remote: Resolving deltas: 100% (1/1), done.
    To github-olarn-ad:IT-BANGMOD-INT142-2025/class02-olarnr-ad-sit.git
    68f56e2..bd45a16  main -> main
    ```

16. View your grading on GitHub. You should get 70/100 points.

17. Make changes and commit/push again to get 100 points.
