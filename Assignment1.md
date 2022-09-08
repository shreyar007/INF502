# Git/GitHub Assignment

* **INDIVIDUAL ASSIGNMENT**
* **Due date**: Sept-13th 11:59PM
* **Value**: 100 points counted towards Homework category.

## Description
This assignment is composed of two parts. 
- [Part 1](#Part-1-Dealing-with-git) consists of executing a sequence of commands and giving explanations about the commands you have to run. For each question, please provide appropriate explanation and/or the details requested.

- [Part 2](#Part-2-Using-GitHub) consists of creating a Markdown file on a fork of this course and creating a pull request towards this repo.

### Part 1: Dealing with git

To conduct this, you will have to download [handson.zip](handson.zip) and unzip it in your local machine. **Note:** handson folder is a git repository.

Then, follow these steps:

**On GitHub:**
1. Create a new repository under your GitHub account called *INF502*;
2. Create a file called *"Assignment1.md"*;
3. Copy the questions from this section and paste in your *"Assignment1.md"* file (tip: to copy the questions, click on *"Raw"* at the right-top of this file; this will show you the markdown source);
4. For each empty grey box, please provide an answer to the questions below.
5. Invite me to see your new repository. This will allow you to keep a private repository that only you and me will be able to see.

Your submission is complete when you complete the *Assigment1.md* file with your answers and invite me to your repo.

**On your local machine:** Using the command line, find and access the "handson/" directory (if you didn't download and unzip the file, go back to the beginning of Part 1's instructions). Then, answer the following questions (on your *Assigment1.md* file):

1. List all the branches in this repository and, for each branch, list the commits.

    - Use `git branch` to list the branches in this repository.
    - Use `git checkout` to explore each branch.
    - Use `git log --decorate` to explore the structure of commits.

```
$ git branch
  master
* math

$ git checkout master
Switched to branch 'master'

$ git checkout math
Switched to branch 'math'

$git log --decorate
commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:13:48 2019 -0700

    Adding some more knowledge to the function

commit 654b490a181dedf82dd6deda5f9848d6cca05918
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:12:14 2019 -0700

    Added a draft of A.py

commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:08:47 2019 -0700

     Creating all files (all empty)

```

2. Try `git log --graph --all` to see the commit tree. Paste the result here and write a paragraph to provide an interpretation of what you found.
```
Above is a tree structure. We can see the adiition of a draft named A.py

*   commit 967c07c791237687e0679681a74600b3b716ec9a (master)
|\  Merge: 18931d1 e3c629d
| | Author: Shreya Balasubramanya Raju <sb3292@nau.edu>
| | Date:   Wed Sep 7 19:12:15 2022 -0700
| |
| |     Making a small change here
| |
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| |
| |     Adding some more knowledge to the function
| |
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|
|       Added a draft of A.py
|
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
 Author: Igor Steinmacher <igorsteinmacher@gmail.com>
 Date:   Wed Aug 14 23:12:14 2019 -0700

        Creating all files (all empty)
```

3. Use `git diff BRANCH_NAME` to view the differences from a branch and the current branch. Summarize the difference from master to the other branch.

```
We have the A.py and B.py file.

diff --git a/B.py b/B.py
index e69de29..c63f94c 100644
--- a/B.py
+++ b/B.py
@@ -0,0 +1 @@
+# Another file that will receive a line of code... at least.
```

4. Write a command sequence to merge the non-master branch into `master`.

```
git checkout master
git merge math

```


5. Write a command (or sequence) to (i) create a new branch called `math` (from the `master`) and (ii) change to this branch.

```
git checkout master
git branch math (fatal: a branch named 'math' already exists)
git checkout math

```
   
6. Edit B.py adding the following source code below the content you have there.
```
print 'I know math, look:'
print 2+2
```

7. Write a command (or sequence) to commit your changes.
```
git add B.py
git commit -m "addition of two lines to B.py on math branch"

```

8. Change back to the `master` branch and change B.py adding the following source code (commit your change to `master`):
```
print 'hello world!'

git checkout master
git add B.py
git commit -m "adding one line to B.py on master branch"
```

9. Write a command sequence to merge the `math` branch into `master` and describe what happened.
```
Already up to date 

git checkout master 
git merge math

```
   
10. Write a set of commands to abort the merge.
```
git merge --abort

```
   
11. Now repeat item 9, but proceed with the manual merge (editing B.py). All implemented methods are needed. Explain your procedure.
```
No errors are seen. None of the files are copied.

```

12. Write a command (or set of commands) to proceed with the merge and make `master` branch up-to-date.
```
git checkout master
git merge math
git rebase

```

13. Complete Part 2. Then, come back here and answer the following:
Report your experience of submitting the Part 2. Please, include the steps you followed, the commands you used, and the hurdles you faced (within the file you created for the **Part 1**).
```
Part 2 helped me in learning the functionalities of github and how to use it. Found this assignment very helpful. I first forked this repo and created a markdown file with my name. I added the details of the paper which I read and commited the file. Later I then created a pull request for this repo and checked if it was sucessfully saved. One of the difficulties I faced was getting familar with working on GitHub.

```

### Part 2: Using GitHub

The goal of this assignment is to put you in touch with the fork-pull request process, with an extra of dealing a little bit with Markdown. To learn more about Markdown [click here](https://guides.github.com/features/mastering-markdown/).

To complete this submission, follow these steps:

1. Fork the course repository (available [here](https://github.com/chavesana/INF502-Fall22)).

2. Into the students folder, create a markdown file called LASTNAME_FIRSTNAME.md (please change LASTNAME_FIRSTNAME for your actual last and first names). 

3. Use markdown to write a report of the last paper you've read. You can structure your markdown the way you want, but the following information must be there:
- Title
- Venue (journal name/conference)
- Number of pages
- Three outcomes of the paper
- Link to the paper online

4. Commit your file and push to your own GitHub repository (INF502).

5. Create a pull request to the course repository. Your pull request needs to appear [here](https://github.com/chavesana/INF502-Fall22/pulls).

6. Go back to Part 1 and answer the question 13 based on your experience in solving Part 2.

Your Part 2 submission is complete when your pull request is listed in the link above.
