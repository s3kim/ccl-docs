=================================
Git: Versioni Control Tool
=================================

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 

----------------------------------
1. Initial Configuration
----------------------------------

Before using Git, set up your identity (name and email). This information is attached to every commit you make.

.. code-block:: bash

   # Set your global username
   git config --global user.name "Your Name"

   # Set your global email address
   git config --global user.email "your.email@example.com"

   # Verify your settings
   git config --list


----------------------------------
2. Creating & Cloning Repositories
----------------------------------

Start a new repository locally or download an existing one from a remote host (e.g., GitHub, GitLab).

.. code-block:: bash

   # Initialize a new Git repository in the current folder
   git init

   # Clone an existing remote repository onto your machine
   git clone https://github.com/username/repository.name.git


----------------------------------
3. The Basic Git Workflow
----------------------------------

The basic workflow consists of making changes in your **Working Directory**, adding them to the **Staging Area**, and recording them in your **Repository**.

.. code-block:: bash

   # Check the status of your files (untracked, modified, staged)
   git status

   # Stage a specific file for the next commit
   git add filename.txt

   # Stage all modified and new files in the current directory
   git add .

   # Commit staged changes with a descriptive message
   git commit -m "Add feature or describe changes made"


----------------------------------
4. Inspecting History & Differences
----------------------------------

Review changes and commit history to see what was updated over time.

.. code-block:: bash

   # View commit history
   git log

   # View a compact, one-line version of commit history
   git log --oneline

   # View unstaged changes in your files compared to the last commit
   git diff

----------------------------------
5. Branching & Merging
----------------------------------

Branches allow you to develop features, fix bugs, or experiment safely without affecting the main codebase.

.. code-block:: bash

   # List all local branches (* indicates current active branch)
   git branch

   # Create a new branch
   git branch feature-name

   # Switch to an existing branch
   git checkout feature-name

   # Shortcut: Create and switch to a new branch in one command
   git checkout -b feature-name

   # Merge changes from a feature branch into your active branch
   git merge feature-name

----------------------------------
6. Remote Synchronization
----------------------------------

Share your commits with remote repositories or retrieve updates from team members.

.. code-block:: bash

   # Fetch and merge changes from the remote repository
   git pull origin main

   # Push your local commits to the remote repository
   git push origin feature-name

----------------------------------
Quick Reference Summary
----------------------------------

+---------------------------+----------------------------------------------+
| Command                   | Action                                       |
+===========================+==============================================+
| ``git status``            | View modified, staged, or untracked files.   |
+---------------------------+----------------------------------------------+
| ``git add .``             | Stage all current changes.                   |
+---------------------------+----------------------------------------------+
| ``git commit -m "msg"``   | Save staged changes locally.                 |
+---------------------------+----------------------------------------------+
| ``git pull``              | Download latest updates from remote server.  |
+---------------------------+----------------------------------------------+
| ``git push``              | Upload local commits to remote server.       |
+---------------------------+----------------------------------------------+

