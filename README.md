another course "git and gitlab start to finish 7course"


Git
---
  git status
  git add
  git rm 
  git commit -m "blah blah blah"


GIT - Installation and configuration
------------------------------------
 
# yum -y install git


# git config --global user.name "jefftest123"
# git config --global user.email "toto2000@gmail.com"

# git config --system core.editor "/usr/bin/vi"

	creates -->  /etc/gitconfig
		# cat /etc/gitconfig
		  [core]
		  editor = /usr/bin/vi
.




GIT - Creating a Local Repository and Adding Content  (and removing content)
----------------------------------------------------------------------------

  git status
  git add
  git rm 
  git commit -m "blah blah blah"
  
  
  
 
# mkdir repo
# cd repo
# git init .
Initialized empty Git repository in /root/repo/.git/

repo]# ll .git
drwxr-xr-x. 2 root root    6 Feb  6 20:41 branches
-rw-r--r--. 1 root root   92 Feb  6 20:41 config
-rw-r--r--. 1 root root   73 Feb  6 20:41 description
-rw-r--r--. 1 root root   23 Feb  6 20:41 HEAD
drwxr-xr-x. 2 root root 4096 Feb  6 20:41 hooks
drwxr-xr-x. 2 root root   20 Feb  6 20:41 info
drwxr-xr-x. 4 root root   28 Feb  6 20:41 objects
drwxr-xr-x. 4 root root   29 Feb  6 20:41 refs



repo]#  echo "/* This is a valid C source file */" > source.c
repo]# ll -a

drwxr-xr-x. 3 root root   48 Feb  6 20:45 .
dr-xr-x---. 4 root root 4096 Feb  6 20:41 ..
drwxr-xr-x. 7 root root 4096 Feb  6 20:41 .git
-rw-r--r--. 1 root root   22 Feb  6 20:44 README.MD
-rw-r--r--. 1 root root   36 Feb  6 20:45 source.c


repo]# git status
		# On branch master
		#
		# Initial commit
		#
		# Untracked files:
		#   (use "git add <file>..." to include in what will be committed)
		#
		#       README.MD
		#       source.c
		nothing added to commit but untracked files present (use "git add" to track)
repo]#

repo]# git config --global user.name "jeffa"					<-- specifying a user "jeffa"
repo]# git config --global user.email "jeffa@example.com"

repo]# git add .
repo]# git status

repo]# git status
		# On branch master
		#
		# Initial commit
		#
		# Changes to be committed:
		#   (use "git rm --cached <file>..." to unstage)
		#
		#       new file:   README.MD
		#       new file:   source.c
		#
repo]#


repo]# echo "This is a testing file" > test.txt
repo]# git status
		# On branch master
		#
		# Initial commit
		#
		# Changes to be committed:
		#   (use "git rm --cached <file>..." to unstage)
		#
		#       new file:   README.MD
		#       new file:   source.c
		#
		# Untracked files:
		#   (use "git add <file>..." to include in what will be committed)     <-- here is that new file Untracked because 
		#																		   no "git add" command was run for it!
		#       test.txt
repo]#

repo]# git add test.txt
repo]# git status
		# On branch master
		#
		# Initial commit
		#
		# Changes to be committed:
		#   (use "git rm --cached <file>..." to unstage)
		#
		#       new file:   README.MD
		#       new file:   source.c
		#       new file:   test.txt							<-- after the "git add test.txt" command
		#
repo]#



Now we want to commit these files to the repository
run a commit it with a message (use -m option):
--
repo]# git commit -m "This is the initial commit of files to my repo"
		[master (root-commit) 863f5f0] This is the initial commit of files to my repo
		3 files changed, 3 insertions(+)
		create mode 100644 README.MD
		create mode 100644 source.c
		create mode 100644 test.txt
repo]#



repo]# git status
# On branch master
nothing to commit, working directory clean

So lets make a change to the READM.MD file by adding a new line at the end:

repo]# echo -e "\nThis is a new comment after the first commit" >> README.MD

repo]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       modified:   README.MD											<-- Here we are told something was modified!!
		#
		no changes added to commit (use "git add" and/or "git commit -a")		<-- change has not been added to repo in that file
repo]#





repo]# echo "This is a 2nd new file" > test2.txt
repo]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       modified:   README.MD										<-- modified file from earlier
		#
		# Untracked files:
		#   (use "git add <file>..." to include in what will be committed)
		#
		#       test2.txt													<-- newly added file "Untarcked"
		no changes added to commit (use "git add" and/or "git commit -a")
repo]#



 Lets commit the changes, it will modify the  file README.ME but won't do anything for new file test2.txt
 To action the new and "Untracked" filetest2.txt I need to run a "git add test2.txt" and then run a "git commit -a" 

repo]# git commit -a
		[master 842aeb9] Saving the changes to README.ME
		1 file changed, 2 insertions(+)
repo]#

repo]# git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#       test2.txt
nothing added to commit but untracked files present (use "git add" to track)



repo]# git add test2.txt
repo]# git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#       new file:   test2.txt
#
repo]#

repo]# git commit -m "New test file"
		[master d30892e] New test file
		1 file changed, 1 insertion(+)
		create mode 100644 test2.txt
repo]#

repo]# git status
# On branch master
nothing to commit, working directory clean					<-- tada!
repo]#





repo]# mkdir new
repo]# mkdir new1
repo]# echo "test new" > new/new.txt
repo]# echo "test2 new" > new1/new.txt


repo]# git status
		# On branch master
		# Untracked files:													<-- showing new dire "Untracked"
		#   (use "git add <file>..." to include in what will be committed)
		#
		#       new/
		#       new1/
		nothing added to commit but untracked files present (use "git add" to track)
repo]#


repo]# git add .
repo]# git status
		# On branch master
		# Changes to be committed:									<-- now they are ready to commit!
		#   (use "git reset HEAD <file>..." to unstage)
		#
		#       new file:   new/new.txt
		#       new file:   new1/new.txt
		#
repo]#


repo]# git commit -m "Added new source directories"					<-- commit the new directories and files
		[master dfbedec] Added new source directories
		2 files changed, 2 insertions(+)
		create mode 100644 new/new.txt
		create mode 100644 new1/new.txt
repo]#


Now lets delete one file:  test2.txt
and check,..

repo]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add/rm <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       deleted:    test2.txt										<-- ok seeing deleted...
		#
		no changes added to commit (use "git add" and/or "git commit -a")
repo]#


repo]# git commit -m "Removed test2.txt - it was redundant"
		# On branch master
		# Changes not staged for commit:
		#   (use "git add/rm <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       deleted:    test2.txt									<-- still seeing seeing deleted
		#
		no changes added to commit (use "git add" and/or "git commit -a")
repo]#

repo]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add/rm <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       deleted:    test2.txt								<-- humm ,.. still seeing this entry ??
		#
		no changes added to commit (use "git add" and/or "git commit -a")
repo]#


So when you delet a file you're not actually making a commit. Commitments add changes to tracked files
or directories. The act of removing them is a seperate git command:  " git rm "

repo]# git rm test2.txt
rm 'test2.txt'

[root@lab1 repo]# git status
		# On branch master
		# Changes to be committed:
		#   (use "git reset HEAD <file>..." to unstage)
		#
		#       deleted:    test2.txt							<-- Ok still there, guess we need the commit now!
		#
repo]#


repo]# git commit -m "Removed test2.txt - it was redundant"
		[master 4f8db51] Removed test2.txt - it was redundant
		1 file changed, 1 deletion(-)
		delete mode 100644 test2.txt
repo]#

repo]# git status
# On branch master
nothing to commit, working directory clean					<-- ok, it's gone, yeah!!
repo]#





GIT - Logging
-------------
# man git-log


repo]# git status
# On branch master
nothing to commit, working directory clean
repo]#


repo]# git log     <-- gives somewhat verbose output,.. so a lot

Let's go with less verbosage ...

repo]# git log --oneline
		4f8db51 Removed test2.txt - it was redundant
		dfbedec Added new source directories
		d30892e New test file
		842aeb9 Saving the changes to README.ME
		863f5f0 This is the initial commit of files to my repo
repo]#


repo]# git log -p			<-- shows pretty much everything that was done, all changes!! 





So what if we just want to know what was done to a specific file?

repo]# ll
drwxr-xr-x. 2 root root 20 Feb  6 21:19 new
drwxr-xr-x. 2 root root 20 Feb  6 21:19 new1
-rw-r--r--. 1 root root 68 Feb  6 21:00 README.MD
-rw-r--r--. 1 root root 36 Feb  6 20:45 source.c
-rw-r--r--. 1 root root 23 Feb  6 20:50 test.txt			<-- this file for instance ?
repo]#

repo]#  git log -- test.txt
		commit 863f5f0cb0f83ae2749c2c575f302244d91b21a6
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 20:56:42 2019 -0500
		
			This is the initial commit of files to my repo
[root@lab1 repo]#

repo]#  git log --oneline -- test.txt
863f5f0 This is the initial commit of files to my repo



repo]#  git log -- test2.txt								<-- check only for removed file test2.txt
		commit 863f5f0cb0f83ae2749c2c575f302244d91b21a6
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 20:56:42 2019 -0500
		
			This is the initial commit of files to my repo
		[root@lab1 repo]#  git log -- test2.txt
		commit 4f8db51345de247c8bacb0e6cb3e596b51451035
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:37:23 2019 -0500
		
			Removed test2.txt - it was redundant
		
		commit d30892efbad82abc6b3a52d0a6e351752a0c7668
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:14:44 2019 -0500
		
			New test file
repo]#


repo]#  git log --oneline -- test2.txt
		4f8db51 Removed test2.txt - it was redundant
		d30892e New test file
[root@lab1 repo]#



Look for patterns such as the "author" :
		repo]#  git log  --author jeffa						or     git log  --author="jeffa"
		commit 4f8db51345de247c8bacb0e6cb3e596b51451035
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:37:23 2019 -0500
		
			Removed test2.txt - it was redundant
		
		commit dfbedec73109d44d81eecf9c3ac15585dddaf688
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:24:04 2019 -0500
		
			Added new source directories
		
		commit d30892efbad82abc6b3a52d0a6e351752a0c7668
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:14:44 2019 -0500
		
			New test file
		
		commit 842aeb930ae9691f253fb8a55dba7ac2065aa7f6
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:06:39 2019 -0500
		
			Saving the changes to README.ME
		
		commit 863f5f0cb0f83ae2749c2c575f302244d91b21a6
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 20:56:42 2019 -0500
		
			This is the initial commit of files to my repo
repo]#


repo]#  git log  --grep="change"							or 		 git log  --grep change
		commit 842aeb930ae9691f253fb8a55dba7ac2065aa7f6
		Author: jeffa <jeffa@example.com>
		Date:   Wed Feb 6 21:06:39 2019 -0500
		
			Saving the changes to README.ME
repo]#



repo]#  git log  --graph  			<-- good to see when doing "branching"  


 
 
GIT - Cloning  
-------------
 
repo]# cd ..
~]# mkdir workingdir
~]# cd workingdir
workingdir]#


Lets clone the repo from directory "repo]#" to new directory "workingdir]#"
workingdir]# ll -a
,.. nada, zippo...

workingdir]# git clone ~/repo .
		Cloning into '.'...
		done.
workingdir]#

workingdir]# ll -a
		drwxr-xr-x. 5 root root   84 Feb  6 22:14 .
		dr-xr-x---. 5 root root 4096 Feb  6 22:12 ..
		drwxr-xr-x. 8 root root 4096 Feb  6 22:14 .git
		drwxr-xr-x. 2 root root   20 Feb  6 22:14 new
		drwxr-xr-x. 2 root root   20 Feb  6 22:14 new1
		-rw-r--r--. 1 root root   68 Feb  6 22:14 README.MD
		-rw-r--r--. 1 root root   36 Feb  6 22:14 source.c
		-rw-r--r--. 1 root root   23 Feb  6 22:14 test.txt
workingdir]#



lets do some changes in file "test.txt":

workingdir]# vi test.txt
workingdir]#
workingdir]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       modified:   test.txt
		#
		no changes added to commit (use "git add" and/or "git commit -a")
workingdir]#


workingdir]# git config user.name "dev1"
workingdir]# git config user.email "dev1@example.com"

workingdir]# git add .
workingdir]# git commit -m "Modified local copy of test.txt file"
		[master eaef1a3] Modified local copy of test.txt file
		1 file changed, 4 insertions(+)
workingdir]#


workingdir]# cat test.txt					<-- new file from workingdir repo, a clone of original master repo "repo"
		This is a testing file
		2
		3
		4
		5
workingdir]#

workingdir]# cat ../repo/test.txt			<-- file from original Master repo
		This is a testing file
workingdir]#




Cloning the ssh method, to a remote server:
=========

host1 <-- where current git repo directory is in " ~/workingdir/ " 
host2 <-- where we want to clone repo to

on remote server "host2" do:

host2]# mkdir workingdir
host2]# cd workingdir/
host2 workingdir]# git clone user@host1.mylabserver.com:repo .      <-- ":repo" here will assume home dir ~/repo on host1

enter password: ...



Cloning with github or bitbucket method or via any other 3rd party 
===========

https://github.com/latest123/mytest   
Created my own repo on github.com:     https://github.com/toto2000hello-world.git

~]# mkdir github
~]# cd github
github]# Cloning into 'hello-world'...
		remote: Enumerating objects: 3, done.
		remote: Counting objects: 100% (3/3), done.
		remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
		Unpacking objects: 100% (3/3), done.
github]# ll
drwxr-xr-x. 3 root root 33 Feb  6 23:12 hello-world
[root@lab1 mytest]# cd hello-world/



hello-world]# ll
		-rw-r--r--. 1 root root 48 Feb  6 23:16 README.md
hello-world]#


hello-world]# vi README.md			<-- make sone changes

hello-world]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       modified:   README.md
		#
		no changes added to commit (use "git add" and/or "git commit -a")
hello-world]#


hello-world]# git status
		# On branch master
		# Changes not staged for commit:
		#   (use "git add <file>..." to update what will be committed)
		#   (use "git checkout -- <file>..." to discard changes in working directory)
		#
		#       modified:   README.md
		#
		no changes added to commit (use "git add" and/or "git commit -a")
hello-world]# git commit -a
		[master 6f1a75b] An update to the README.md file
		1 file changed, 5 insertions(+)
hello-world]#



hello-world]# git status
		# On branch master
		# Your branch is ahead of 'origin/master' by 1 commit.
		#   (use "git push" to publish your local commits)
		#
		nothing to commit, working directory clean
hello-world]#



hello-world]# git push origin master
		Username for 'https://github.com': toto2000
		Password for 'https://toto2000@github.com':
		Counting objects: 5, done.
		Writing objects: 100% (3/3), 305 bytes | 0 bytes/s, done.
		Total 3 (delta 0), reused 0 (delta 0)
		To https://github.com/toto2000hello-world.git
		b24e806..6f1a75b  master -> master
hello-world]#



Now goto   https://github.com/toto2000/hello-world   and refresh the link,... and look at the new READM.md file !


Create another git repo and clone the online repo from "https://github.com/toto2000/hello-world.git"

workingdir]# mkdir newclone
workingdir]# cd newclone
newclone]# git clone https://github.com/toto2000hello-world.git
		Cloning into 'hello-world'...
		remote: Enumerating objects: 6, done.
		remote: Counting objects: 100% (6/6), done.
		remote: Compressing objects: 100% (2/2), done.
		remote: Total 6 (delta 0), reused 3 (delta 0), pack-reused 0
		Unpacking objects: 100% (6/6), done.
newclone]#


newclone]# ll
		drwxr-xr-x. 3 root root 33 Feb  6 23:30 hello-world
newclone]# cd hello-world/
hello-world]# ll
		-rw-r--r--. 1 root root 48 Feb  6 23:30 README.md
hello-world]# cat README.md
		# hello-world
		Just another repository
		1
		2
		3
		4
		5
hello-world]#



































