Git, Data carpentry/Environmental informatics
========================================================
author: Daniel Reuman
date: February 2018
css: ReumanRpresStyle.css



Introduction
===
type: redslide

What Git is for
===
type: redslide
- Version control generally, and git as a specific and very popular application... 
- Provides a complete solution for the problems of tracking and storing changes made to multi-author, text-based documents
- With facilities included for 
  - attributing changes 
  - comparing revisions 
  - reverting to earlier versions 
  - branching and  merging revisions 
  - tagging revisions
  - extensive other functionality

What Git gets you
===
type: redslide
- You and others write and edit a collection of documents (most commonly code) over time
- You can (in the main):
  - Each of you make edits any time you want from anywhere you want (with an internet connection) to any part of the code 
  - Edit conflicts (explain) are managed effectively
- Return to the version that was current at any given time in the past, for the whole repository or for any subset of it
- Track who made each change, and they can enter explanatory notes
- Branch and merge

What else you can do (scientifically)
===
type: redslide
- If you are willing to put your data in the version control, then you can just name a version number associated with results and know in complete detail what version of the code was used to produce those results
- Every time a change is made, there is a new version number, so the version number makes it possible to get the complete state of the repo at that time
- Makes *real* and *exact* reproducibility possible

One (awful) non-git approach
===
type: redslide
- Dated file names
- But this stinks
  - Too many files
  - If you update one of 20 files do you make a new version number for all files?
  - Referring to file names within the code becomes difficult
  - What if more than one person is working on it? It's a nightmare.

Another (awful) non-git approach
===
type: redslide
- Dropbox
- But this stinks
  - Cannot really get history
  - Conflicts are poorly managed
  - Dropbox was never intended for this purpose

Plug for version control
===
type: redslide
- Basically, git is a one stop shop for keeping track of edits to code (which in our use of R markdown is not just code but also the paper)
- This is what software engineers use, and, increasingly, quantitative biologists 
- OK, so using Subversion (SVN) is about as good as git - there is more than one piece of version control software
- Git is popular, and has some advantages over SVN

A Git setup
===
type: yellowslide

What a Git setup consists of (minimal)
===
type: yellowslide
- Your _working copy of the code_
  - This is the most current version
  - Can have as many files as you want, in as many directories as you want
  - Sits on your computer's hard drive
- Your _local copy of the repository_
  - This is not ordinary visible through, say, Windows Explorer - the Git software keeps it hidden
  - But is has the complete version history in it - all changes ever made to your files 
  - Storage is very effecient (why?)
  
Additional cloud component of Git setup
===
type: yellowslide
- If you want to collaborate with others on the same code...
- And/or if you want a remote backup...
- You also need a _remote/cloud copy of the repository_
  - I always have one of these - I won't even teach you how to do git without one of these (don't know), though it is possible
  - Hosted on a remote server (we use github.com)
  - You get free *public* repo's
  - Academics can get free *private* repo's

Review of setup components and terminology
===
type: yellowslide
- Working copy of the code
- Local copy of the repository
- Remote/cloud copy of the repository

Getting set up with Git 
===
type: blueslide

Setup to the command-line interface
===
type: blueslide
- You should have already set up a github.com account for yourself, and asked for private repositories if you want them
- You should have already installed git on your machine, and obtained access to a command-line interface
- You know you have succeeded if you can type "git" at the command line and get a list of commands git can perform

Starting and cloning a repository
===
type: violetslide

Starting a repository
===
type: violetslide
- Go to github and start a new repository for yourself
- Please name it `<lastname>_dcei` where you substitute your last name for `<lastname>` here. This is important because you will later be sharing your  repository with us, and we will need to be able to tell them apart.
- `dcei` stands for this course
- By the way, whenever I write something in `<>` it means replace it with an appropriate value specific to you

Cloning a repository
===
type: violetslide
- This will bring a working copy of the repository (which is empty so far) to your machine
- First select a location on your machine where you want your local copy of your git repo for this course to be located
- This should be inside your folder for this course (yes, you should have such a folder)
- It should NOT be on your desktop (nothing should be on there besides links to software, really)
- Then get there in your terminal window
  - `ls`, `cd x`, `cd ..` (linux, probably mac)
  - `dir`, `cd x`, `cd ..` (windows)

Cloning a repository
===
type: violetslide
- Then find the url for your repository on github and copy it to your clipboard
- Then, in the terminal, in the desired location, type: `git clone <url>`
- A bunch of stuff should happen and a copy of the repo should appear
- This is the working copy of your repository

Adding files
===
type: orangeslide

Adding files to your repo
===
type: orangeslide
- Use `cd` to change your terminal directory to the directory of your git working directory
- Type in `git status` to the terminal prompt  
- Save any old text file there (What counts as a text file? Hint: a Word doc does not.)
- Type `git pull` to update your local repo and working copy before changing it
- We will discuss this more later

Adding files, continued  
===
type: orangeslide
- Type `git add <filename>` to the terminal where `<filename>` is the name of the file you saved
- Now type `git status` again in the terminal
- Now the file is "staged for commit" to the local copy of the repository
- That is what the `git add` command did

Adding files, continued  
===
type: orangeslide
- Type `git commit -m"adding a file"`  
- This commits the file to the local copy of the repository
- If there had been any other files staged for commit, they would have committed too
- Type `git status` again to see the change
- The `-m` option is required and very important. Once there are many commits it helps a lot to have a brief description of what each was, in case you need to find a particular old version again.

Adding files, continued
===
type: orangeslide
- Type `git push`
- Enter the necessary login information for github
- Note: you can configure your git so this is supplied automatically and you do not have to type it every time
- This pushes the changes you recently committed to the local copy of the repository up to the cloud copy

Adding files, summary
===
type: orangeslide
- Once the file is saved on your local machine in one of the subdirectories of the project...
- `git pull`
- `git add <filename>`
- `git commit -m"<informative message>"`
- `git push`
- You can do `git status` whenever you want to verify steps

The standard workflow
===
type: greenslide

The standard workflow
===
type: greenslide
- `git pull`
- Work and modify files locally, typically five minutes to a day of work, no more
- `git pull` (yes, do it again, even if you "know" no one else has made changes)
- Do `git add` for any new or modified files (stages them for commit)
- `git commit -m"<message>"`
- `git push`
- Repeat

Why we always do a `git pull` before a `git commit` 
===
type: greenslide
- In case someone else changed the files we changed
- "Conflicts" can only be resolved on a pull, not on a commit
- What are conflicts?
- Even if you "know" no one else has made changes, get into the habit of *always* **always** doing a pull right before doing a commit

How often should I commit?
===
type: greenslide
- Before you leave for computer for any length of time more than 10 minutes
- Whenever you have completed a small task
- Never less than once a day, usually more if you work all day
- There is really no cost to commits, so you should err on the side of doing a lot of them
- How git efficiently stores changes (explain)

Some other topics
===
type: indigoslide

What kinds of files go in git?
===
type: indigoslide
- Text files only. This includes:
  - .csv but NOT .xls
  - .txt but not .doc or .docx
  - .R, .Rmd, .Rpres but NOT .RData
  - NOT pdf or jpg or git or png
  - Basically anything you can open with a text editor like Wordpad or emacs or gedit
- Git can store changes to text-based docs effeciently
- Not so for other docs (explain)

Do I put my data in git?
===
type: indigoslide
- If it is not text-based, typically no
  - especially if it is large files, and it might be changed through time a lot, and you have a small quota in your repo
  - perhaps yes if you are very certain it will not change and you want it to be easily ported to all users, and it is not too big (but there are also other ways to do this)
- If it is text-based, and not too big a file
  - Then this can be a good idea, I think
  - You can track any possible revisions in your data, as well
  - You can indentify which version of the data and code correspond to a set of results by keeping the version number

Minimizing conflicts 
===
type: indigoslide
- Conflicts occur when two users edit the **same line** of the **same file** at the same time
- They are pretty uncommon
- We will learn later what to do if they happen
- You can minimize them by doing fairly frequent commits
- You can minimize them with a bit of communication with your colleagues

Carriage returns
===
type: indigoslide
- If you are using an editor that wraps lines of text, you may not put carriage returns in when writing the text components of an R markdown
- This can be sub-optimal
- Then your "lines" are actually whole paragraphs
- Since conflicts occur when two users edit the same line, if lines are longer then conflicts are more frequent!

Adding a directory
===
type: indigoslide
- To add a directory (subdirectory, subsubdirectory, etc.) to a repo...
- Create the directory with Windows Explorer (or similar)
- Put a new file in it, and do a `git add` on the file, then commit
- The directory gets added automatically
- Won't be added to the repo if there are no version-controlled files in it

Proper file management
===
type: redslide

File removal
===
type: redslide
- To remove a file, you cannot just delete it with Windows Explorer (or similar)
- It will be resurrected the next time you do a pull!
- Instead use `git rm <filename>` from the terminal
- The file disappears from your working directory but is still in your repo (as it should be)
- It will not reappear when you do a pull

Renaming a file
===
type: redslide
- You cannot just move or rename a file with Windows Explorer
- If you rename a file this way, when you next do a pull the old file will be back under the old name and the new file will no longer be under version control!
- Do `git mv <old_filename> <new_filename>` instead
- This also avoids breaking the revision history
- Constantinople changed to Istanbul, but the history is the same!

Moving a file
===
type: redslide
- If you are in the same directory as the old file...
- Use `git mv <old_filename> <new_path/new_filename>`

Terminology review
===
type: yellowslide
- Working copy of code
- Local copy of repository
- Remote/cloud copy of repository
- git clone 
- git pull, push, commit, add, status
- ls, cd, dir
- git rm, mv

Quick exercise
===
type: blueslide
- Get with your neighbors in trios or foursomes
- One of you (person A) invite the others onto your github repo
- Then that person (A) does a pull, add a file, commit, push
- The others (B-D) pull and see the change
- Then the others (B-D) change separate lines of the file and then pull, add the changed file, commit, push
- Then A pull to see the changes
- Play around with it for a while but avoid conflits for now
- A can then remove the file from version control (git rm)
- Then A can un-invite B-D from the repo

<script type="text/x-mathjax-config">
   MathJax.Hub.Config({  "HTML-CSS": { minScaleAdjust: 125, availableFonts: [] }  });
</script>
