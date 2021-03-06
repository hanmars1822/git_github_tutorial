# Git and GitHub Tutorial
### Written by Colette Salyk, Assistant Professor of Astronomy, Vassar College

# Who is this tutorial for?
This tutorial is written for a scientist who is:

1.  new to git and GitHub
2.  wants to use some basic version control and back up all of their code online (on GitHub)
3.  wants students to be able to access that code, download it to their own machine, and also download any updates the instructor adds.

I wrote this bare-bones tutorial to provide an extremely simple set of instructions to someone like me wanting to get started with Git and GitHub.   I found that most instructions online had more info than I needed to get started, and were geared more towards developers working on teams. For my purposes, I do limited version control; instead, using Git and GitHub is most useful because it allows me to keep my code safely in the cloud, allows me to have have multiple machines using the same, up-to-date code, and allows me to share and update code with students.  

I do not deal here with version control, collaborative editing, or any other features of Git.  For information about these features, or for more
detail on the process I describe here, there are many resources available online.  

# The tutorial
All commands given below are assumed to be on the command line.

In addition, this tutorial assumes you have some set of (perhaps python) code that you plan to use.  This set of code is referred
to as a *package*, and will be stored in a *repository*. 

* **Step 0a (for the instructor):** Make sure git is installed on your machine. To see if you already have git installed, type:
```  
git --version
```  
If not, go to https://git-scm.com/downloads to download and install.

* **Step 0b (for the instructor):** Sign up for an account on GitHub. Note that if you are a professor at an academic institution, you are eligible for GitHub pro! To sign up for GitHub, go to https://github.com/ and click on “Sign up”.  To apply for educator benefits, find more info here: https://education.github.com/.

* **Step 1 (for the instructor):** Set up your directory.
  * Create a new directory to hold all of your code for your new package.  Typically, in addition to all of your python code files, you want your package directory to have the following files:
    - LICENSE : A text file describing what license your code has
    - README.md : A file describing your package, including some simple usage statements.  The .md suffix means it’s in “Markdown” format. If you write it in Markdown, then it will show up nicely formatted on GitHub.
    - \_\_init\_\_.py : An initialization file for your package.  This defines what happens if a user types
```
import yourpackagename
```  
As an example, if you have a package named yourpackagename and it has a file called yourpackagename.py and a function called yourroutine, you might want to write 
```
from .yourpackagename import yourroutine
```
  The dot means that the package is in that directory.

* **Step 2 (for the instructor):** Initialize your directory for git and do your first commit. To initialize your directory, type
```  
    git init
```  
To perform your first commit, first type:
```  
    git add -A 
```  
The -A says you want to keep track of changes to all files.  
Then type:
```  
    git status 
```  
to see which files git thinks have been modified, and which branch you’re on.  By default, you’ll be on the “master” branch.  (This is important for version control, which I won't be covering here.  But if you were trying out different versions of code, you would create other branches with different names).   After this, type:
```  
    git commit -m "Initializing directory"
```  
to commit (save) your changes.  The -m means you are adding a message to your commit, and the message is given in the quotes.

* **Step 3 (for the instructor):** Get your new package onto GitHub.

  -Go to Github and login.

  -In the upper right, click + symbol to add a repository.  Write the name of your repository (the same as the name of your local package name).  Do NOT add any init files, README files, etc. to this repository when requested, since you already have them in your local directory, and you don’t want GitHub to get confused.

Copy the code from “push an existing repository from the command line”, or simply type the code below, replacing remoterepositoryURL with the address of your GitHub repository.
```  
git remote add origin remoterepositoryURL
```  
The remoterepositoryURL will have the format https://github.com/yourusername/yourpackagename.git.  This command defines the remote repository named “origin” to be your package on GitHub.  (In other words, it tells git where online you want to store your code).

Still in your local package directory, type:
```  
git push -u origin master
```  
This command will copy your code from your local directory to the GitHub repository. Your code is now safely stored in the cloud!

* **Step 4a (for the student):** Have your student also install git and sign up for GitHub.  Have them go to https://git-scm.com/downloads to download and install.  To sign up for GitHub, go to https://github.com/ and click on “Sign up”.

* **Step 4b (for the student):** If your student is using python code for the first time, make a new directory and add it to the python path.  Have the student create a new directory to hold all of their python code.  For example, my directory is /Users/myusername/mypy

Have the student add this directory to their python path.  On a Mac, this is done by adding the line:
```  
export PYTHONPATH=$PYTHONPATH:/Users/myusername/mypy
```  
to their .bashrc file.  On a PC, this is done by defining a new System Variable called “PYTHON PATH”.

* **Step 5 (for the student):** Your student now needs to copy your code to their local machine, and configure git to pull future changes.  Have the student go to the code location on GitHub (for example, https://github.com/yourusername/yourpackagename).  Have them click ``Clone or download”.  In clone with HTTPs section, copy clone URL for repository (usually https://github.com/yourusername/yourpackagename.git).  In a terminal window, have student go to the location where they want to save code.
Then have them type:
```  
git clone yourrepositoryURL
```  
replacing yourrepositoryURL appropriately.  They’ll now have a local clone of your repository.  By default, it’ll save the clone to a directory with the same name as the repository.  To configure git so that it knows where to pull future changes you might make to the code, have them go into the new repository directory and type:
```  
git remote add upstream yourrepositoryURL
```  
This adds a new external repository named “upstream”, which points to your repository.  In other words, git now knows where online to look for any code updates.

* **Step 6 (for the instructor):** Make code modifications and update both your local copy and your GitHub copy.    After you’ve made some code changes that you’d like to keep track of, type:
```  
git add -A 
```  
to make git aware of those changes.  Then type:
```  
git commit -m “Description of the code changes I made” 
```  
to commit the changes.  Now, your local copy is updated.

To update your changes on GitHub, type:
```  
git push origin master
```  
This copies all of your local changes (assuming you’re still on the “master” branch) to the GitHub url.

* **Step 7 (for the student)**: Now your student can pull code changes (i.e., update their local code), after you’ve made code modifications.  Have the student go to the directory holding the local copy of your code.  Then, have them type:
```  
git pull upstream
```  
This will update the code on their local machine, so that it matches what you've put on GitHub.  They'll now have up-to-date code!  