Revision Control & File Sharing:
================================
Overview
--------

### git -  Software Configuration Management (SCM) / Source Control Management (SCM) / Version Control System (VCS)
  * #### Branching and Merging
    + The Git feature that really makes it stand apart from nearly every other SCM out there is its branching model.
    + Git allows and encourages you to have multiple local branches that can be entirely independent of each other. The creation, merging, and deletion of those lines of development takes seconds.
    + This means that you can do things like:
      - **Frictionless Context Switching.** Create a branch to try out an idea, commit a few times, switch back to where you branched from, apply a patch, switch back to where you are experimenting, and merge it in.
      - **Role-Based Codelines.** Have a branch that always contains only what goes to production, another that you merge work into for testing, and several smaller ones for day to day work.
      - **Feature Based Workflow.** Create new branches for each new feature you're working on so you can seamlessly switch back and forth between them, then delete each branch when that feature gets merged into your main line.
      - **Disposable Experimentation.** Create a branch to experiment in, realize it's not going to work, and just delete it - abandoning the work—with nobody else ever seeing it (even if you've pushed other branches in the meantime).
  * #### Distributed
    + One of the nicest features of any Distributed SCM, Git included, is that it's distributed. This means that instead of doing a "checkout" of the current tip of the source code, you do a "clone" of the entire repository.
  * #### Multiple Backups
    + This means that even if you're using a centralized workflow, every user essentially has a full backup of the main server. Each of these copies could be pushed up to replace the main server in the event of a crash or corruption. In effect, there is no single point of failure with Git unless there is only a single copy of the repository.
    Any Workflow
    + Because of Git's distributed nature and superb branching system, an almost endless number of workflows can be implemented with relative ease.
  * #### Free and Open Source
    + Git is released under the GNU General Public License version 2.0, which is an open source license. The Git project chose to use GPLv2 to guarantee your freedom to share and change free software---to make sure the software is free for all its users.

### GitHub - Code sharing and collaboration platform
    Open source
      Free public repositories
      Paid private repositories

Purpose:
--------
Learn Revision Control System (RCS) / Source Control Management (SCM)
  1. Software that does RCS/SCM (e.g. git)
  2. Software to provide group and/or remote access to repositories
    * (e.g. GitHub)

Git Features:
-------------
1. **Online Offline**
  * Can be used online/offline.

2. **Version Control**
  * Commit: one version of the file
    + Saves the current file as a new version
    + New document versions are saved manually
    + Creating a new document versions is referred to as a commit
    + Commits should be commented to explain what was changed
    + One Commit Per Logical Change:
      - The amount of changes between commits should not be to large
        (i.e. hard to keep track of all the changes)
      - New commits should be easy to follow and understand what has changed.
      - The commit message should explain the single logical change
    + The number of commits can be very large
    + Each commit will have a Commit ID, Author, Date, and Comments
      - Example Commit ID: b0678b161fcf74467ed3a63110557e3d6229cfa6
  * Repository: Tracking across multiple files
    + All files in the repository are saved whenever something is commit
    + Location: The git repository is stored in the .git directory
      - (dot files/folders are often hidden by the operating system)

  * Three Main Sections of git
    * Working Directory
      - A single checkout of one version of the project
    * Staging Area
      - Contains information abou what will go into the next commit
    * .git
      - directory/server where repository is stored

Git Behavior:
  Git commands affect the branch that is currently checked out.  If a command takes
  two branches, the order that the branches are entered doesn't matter. Example,

  Example 1: If the master branch is checked out then
    git merge master add_cloud_storage
  would merge the changes from add_cloud_storage into the master. This is what
  you would do if you wanted to add a new feature to the main code.

  Example 2: If the add_cloud_storage branch is checked out then
    git merge master add_cloud_storage
  would merge the changes from master into the add_cloud_storage branch. This is
  what you would do if you wanted to keep your alternate branch up to date with
  all the officially accepted changes from your master code.


Git Commands:
    git log
        Example: git log
          returns a list of all the commits with their Commit ID, Author, Date,
          and Comments
        Example 2: git log --graph --oneline <branch1> <branch2>
          Add vertical lines showing the branching paths
        Example 3: git log -n 1
          -n stands for number of commits to be shown, in this case 1.
        Note 1: Press q to quit
        Note 2: "log" will only show commits prior to the current HEAD

    git diff <commit_id_older> <commit_id_newer>
        Example 1: git diff <commit_id_older> <commit_id_newer>
          Shows differences between 2 versions  (commits) of a file
        Example 2: git diff
          Compares the files in the "working directory" with the files in the
          "staging area"
        Example 3: git diff --staged
          Compares the files in the "staging area" with the head of  the commits
          Note: --staged = --cached
        Note: For colored diff, git config --global color.ui auto

    git clone <repo path/link>- makes a copy of a repository
         Example: git clone https://github.com/udacity/asteroids.git

    git checkout - Converts all files to the state they were in
        during the chosen commit.  Think of it as checking out a specific
          version of the files
        Example 1: git checkout b0678b161fcf74467ed3a63110557e3d6229cfa6
        Note 1: Whichever commit you checkout becomes the new HEAD
        Note 2: "log" will only show commits prior to the current HEAD
        Example 2: git checkout <branch_name>
          Makes the current branch the head
        Example 3: git checkout -b <new_branch_name>
          Creates a new branch and checks it out.
          Equivalent  to the following 2 commands:
            git branch <new_branch_name>
            git checkout <new_branch_name>

    git init - Initialize (Create) a new repository
      The directory that you run git init in becomes the home directory for
        that repository.
      The .git directory will be created in the directory where git init is ran

    git status - Returns  the status of the git repository
      Provide info on branch status, commit status, files tracked/untracked

    git add <filename> - add file or files to the staging area so they can be
        added at the next commit
      Example: git add index.c
      Example: git add *.c
    git add <directory> - recursively adds all the files in the directory
      Example: git add css

    git branch - commits are allowed to progress down different labels.
        These labels are called branches.
      Example 1: git branch
        Returns all the available branches.
      Example 2: git branch <new_branch_name>
        Creates a new branch.  This creates a pointer to the same commit as you
        are currently on.
      Note 1: Branch naming convintions
        one name -> branch name
        name1/name2 -> remote_name/branch_name (e.g. origin/master)
          this combo branch name is placed on the local commit to represent the
          last known remote commit with that branch name
      Note 2: Branches can be thought of as pointer that can be moved to point
        at different commits

    git show <commit_id>
      Shows the diff between a commit and its parent.  Useful when two branches
      have been merged and there are commits from the other branch in between
      the commit and its parent.

    git merge checked_out_branch_name branch_name_to_be_merged_in
      Merges a branch with the currently checked out branch
      Note 1: if the checked out branch is the master then the other branched
              will be merged into the master (becoming part of the master).
      Note 2: If the checked out branch was an experimental branch and the
              other branch was the master then the master will be merged into
              the experimental branch.  (Keeping the experimental branch up to
              date with changes in the master, but the master will still not
              have the experimental changes.)

    git remote add <chosen remote repository name> <remote repository address>
      - creates a name used to reference/connect a remote repository
      Ex 1: git remote add origin https://github.com/VicVis/reflections.git
        Note 1: If you only have 1 remote it is standard to name it "origin"
        Note 2: the address seems to be the webpage address plus ".git"
        Note 3: When a new repository is created in GitHUB it tells you what
          the address is
      Ex 2: git remote
        - list the names of the remotes that are connected
      Ex 3: git remote -v
        - verbose output gives remote name push/fetch locations

    git fetch <remote_name> <branch_name>
      Adds the remote branch to the local repository with the local branch name
        remote_name/branch_name. If there is a conflict it is added as a new
        branch.
      Ex 1: git fetch origin master
        branch will be named origin/master

    git push <name_used_to_refer_to_the_repository> <branch_name>
      - takes a branch from your current repository and
        sends it to the chosen repository

    git pull <name_used_to_refer_to_the_repository> <branch_name>
      - takes a branch from your chosen repository and
        brings it to the current repository
      Note 1: git pull is the equivalent of git fetch followed by git merge

    git status
      Gives the status of your staging area and working directory.
        Unmerged conflicts would be shown.
        What needs to be committed would be shown.
        What has been modified but not added or committed
      Ex 1: output from git status
        On branch master
        Changes not staged for commit:
          (use "git add <file>..." to update what will be committed)
          (use "git checkout -- <file>..." to discard changes in working directory)

                modified:   git_bash_notes

        no changes added to commit (use "git add" and/or "git commit -a")



Git Bash Layout/Formatting


Software:
  Git based rcs/scm:
    Git Command Line:
      Git BASH (Linux Style Command Line)
      Git Shell (Windows Style Command Line)
    Git with GUI
      Git GUI (Windows Style Graphical User Interface):
      GitHub Desktop
      GitEYE
      GitKraken
      SourceTree
      Git Extensions
      Giggle
      SmartGit
      Tower
      (many others)

	Git based repositories/servers
    GitHub -
      Public Repositories: free
      Private Repositories: paid monthly
      Space: unlimited
      Host your own server: no
    GitLab
      Public Repositories: free
      Private Repositories: free
      Space: unlimited
      Host your own server: free
    BitBucket
      Public Repositories: free
      Private Repositories: paid monthly
      Space: unlimited
      Host your own server: $10 purchase price for small team

  Code Searching Software
    SourceGraph - Search personal and public code (primarily GitHub)

  Text Editors:
    Atom - Simple text editor created by GitHub
      Note: like a reimagined emacs, not a rich text editor like word
    Brackets -
    Sublime -
    Vim -
    Emacs -
    Notepad++ -
