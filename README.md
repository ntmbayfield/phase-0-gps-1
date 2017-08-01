# phase-0-gps-1

###**git clone <URL of repository to be cloned>
clones repository from the specified URL to your Github account

###**cd <directory name>
change from the current working directory to the one specified in the command

###**ls
lists files and folders present in current working directory

###**touch <file name>
create a file with the name <file name> in the current working directory

###**git push origin master
send changes made on the local repository to the master branch hosted on Github

###**git checkout -b <branch name>
create a new branch with the name <branch name> and switch to that branch

###**git status
tells you what stage in the git commit process you are at

###**git add <file name.ext>
adds the specified file or folders to the staging area to be committed

###**git commit -m <"commit message">
commits the files that are currently in the staging area and records the commit message specified in the command

The command git-status is used to understand what stage the files in a repository are at.  You use the command git add filename.ext to move a file to the staging area from being untracked.  You can run the git-status command again to see that the file has now been added to the staging area. The final stage is to commit the change we have made. The command used to do this is git commit -m “Message_explaining_what_we_did_and_why.”  This human-readable explanation will go alongside Git's own record of the change and the file structure snapshot at that point.

If you think of Git as taking snapshots of changes over the life of a project, git add specifies what will go in a snapshot (putting things in the staging area), and git commit then actually takes the snapshot, and makes a permanent record of it (as a commit).

Git is a system that saves the contents of the files in your project. It can reproduce the contents of your files exactly as you originally saved them, exactly. If you had a semicolon on line 10 of your file six versions ago, when you retrieve the file six versions back, you'll find a semicolon on line 10 in the recovered file, exactly as you saved it six versions ago.

Git is able to save a file's content exactly as you originally saved it due to the National Security Agency. They invented a two-way, unique, content encryption algorithm called "SHA-1" that turns any document's contents into a unique, 40 hex character compressed blob.

It's two-way, because with the SHA-1, 40 character, hex hash you can go the other way, and reproduce the contents of the file.  It is unique, because if you remove that semicolon on line 10, you'll have a completely different SHA-1 value for the contents. The result is we have one hex name, that represents the entire contents of a file that is much easier to manage and track.

It allows Git to quickly determine whether a file has changed by just looking at the name. It also means, since all SHA-1 is calculated the same on every computer, for every user, you can quickly and easily copy, or clone, and move an entire project to another computer, and it will be identical to the original content, exactly.  In Git, these hash numbers are stored in your .git/objects database that you create when you run "git init" to start your database repository.

Let's go over some Git terms and we'll put it all together.

Your "working directory" is where you work, where you edit files, rename your files, make new directories, and develop your project as you work day by day. If you open up a file in an editor and make a change, you've made a change to your working directory.

Your "index" is just one file in your .git directory. It can grow quite large depending on the number of commits. It is a listing of each file you have committed, and the files you have staged, or are ready to commit, in your repository. Each file takes one line in the index that contains the files SHA-1 hash, the directory path, the file name of the file, and its permissions.

When you do a "git add" command, git encrypts the files in your working directory that have changed contents into their new SHA-1 hash, adds the compressed SHA-1 hash to .git/objects store, and adds that file as a line in the index file ready for committing. That file is now in the index, or staged, and ready to be committed. You'll notice I said the files that have changed. Git doesn't need to encrypt files that have not changed. It already has the SHA-1 hash for them.

When you commit, Git really has four objects it tracks that form a hierarchy of objects: a blob, a tree, a commit, and a tag. At the bottom is the blob that is the contents of your file as a SHA1 hash. The tag is just a way to give a particular commit a special name, and is attached to the commit object, which leaves us the tree and commit object to consider.

The tree object is how Git keeps track of file names and directories. There is a tree object for each directory. The tree object points to the SHA-1 blobs, the files, in that directory, and other trees, sub-directories at the time of the commit. Each tree object is encrypted into, you guessed it, a SHA-1 hash of its contents, and stored in .git/objects. The name of the trees, since they are SHA-1 hashes, allow Git to quickly see if there's been any changes to any files or directories by comparing the name to the previous name. Pretty slick.

"Git commit" only works with the index, not your working directory. One of the reasons is the SHA-1 hash of the file is created during "Git add". During the commit, the tree objects are built up, and we end up with one name for an entire tree of blobs and trees, the top tree object, which we'll use with our commit object.

The commit object keeps track of the physical state of the tree at a given point in time, when you commit. It consists of the commit name, a SHA1 hash, the previous commit name, so you can track your history of commits, the SHA-1 of current top tree with all the changes for that commit included, the original author of the initial commit, the person doing the commit, and a comment describing the commit. Remember, there can be more than one editor of a file, other than the original author. The commit object keeps track of both.

We have a hierarchy. The Git commit object points to the previous commit, and the top git tree. The top git tree points to all the tree objects under it and all files. The SHA-1 file names point to the contents. We have a history. You can easily go back and get the contents of a file if you mess up the code really bad in your working directory file by bringing back your last commit of the file, with a simple git checkout "the file", nice, and the reason to use a version control system, like Git.

Committing in Git is about working with the index to make a snapshot of your project at the time of the commit. Since the Git index has the SHA-1 of a file and its path and file name, it is used to compare the previous commit with files ready to commit, and saving anything changed along with all that was not changed by reference to the SHA-1 name.

