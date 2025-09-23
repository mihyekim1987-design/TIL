vagrant@ubuntu:~/Documents/dev$ mkdir mc-test
vagrant@ubuntu:~/Documents/dev$ ls
TIL  branch-616  branch-practice  first-repo  markdown.md  mc-test
vagrant@ubuntu:~/Documents/dev$ cd mc-test
vagrant@ubuntu:~/Documents/dev/mc-test$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
  1 <<<<<<< HEAD
  2 b
  3 =======
  4 c
  5 >>>>>>> stem
~
~
"test.txt" 5L, 38B                                                                                                          1,1           All
  1 bc
hint:
hint: 	git branch -m <name>
  1 Merge branch 'stem'
  2
  3 # Conflicts:
  4 #   test.txt
  5 #
  6 # It looks like you may be committing a merge.
  7 # If this is not correct, please run
  8 #   git update-ref -d MERGE_HEAD
  9 # and try again.
 10
 11
 12 # Please enter the commit message for your changes. Lines starting
 13 # with '#' will be ignored, and an empty message aborts the commit.
 14 #
 15 # On branch master
 16 # All conflicts fixed but you are still merging.
 17 #
 18 # Changes to be committed:
 19 #   modified:   test.txt
 20 #
~
~
"~/Documents/dev/mc-test/.git/COMMIT_EDITMSG" 20L, 440B                                                                     1,1           All
  1 Merge branch 'stem'
Initialized empty Git repository in /home/vagrant/Documents/dev/mc-test/.git/
vagrant@ubuntu:~/Documents/dev/mc-test$ touch test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git commit -m "test a"
[master (root-commit) 9eec33a] test a
 1 file changed, 1 insertion(+)
  1 bc
~
~
"test.txt" 1L, 3B                                                                                                           1,1           All
  1 t
 create mode 100644 test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git branch stem
vagrant@ubuntu:~/Documents/dev/mc-test$ git branch
* master
  stem
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
  1 bc
~
~
"test.txt" 1L, 3B                                                                                                           1,1           All
  1 u
vagrant@ubuntu:~/Documents/dev/mc-test$ git commit -m "test b"
[master f60e1c0] test b
 1 file changed, 1 insertion(+), 1 deletion(-)
vagrant@ubuntu:~/Documents/dev/mc-test$ git switch stem
Switched to branch 'stem'
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git commit -m "test c"
[stem 495f105] test c
 1 file changed, 1 insertion(+), 1 deletion(-)
vagrant@ubuntu:~/Documents/dev/mc-test$ git switch master
Switched to branch 'master'
vagrant@ubuntu:~/Documents/dev/mc-test$ git merge stem
Auto-merging test.txt
CONFLICT (content): Merge conflict in test.txt
Automatic merge failed; fix conflicts and then commit the result.
vagrant@ubuntu:~/Documents/dev/mc-test$ cat test.txt
<<<<<<< HEAD
b
=======
c
>>>>>>> stem
  1 <<<<<<< HEAD

2 t
  3 =======
  4 u
  5 >>>>>>> 61363f6 (rebase test u)

~
"test.txt" 5L, 57B                                                                                                          1,1           All
  1 u from t
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git commit
[master f4cdf49] Merge branch 'stem'
vagrant@ubuntu:~/Documents/dev/mc-test$ git branch -D stem
Deleted branch stem (was 495f105).
vagrant@ubuntu:~/Documents/dev/mc-test$ git branch
* master
vagrant@ubuntu:~/Documents/dev/mc-test$ git branch stem2
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git commit -m "rebase test t"
[master bb37a81] rebase test t
 1 file changed, 1 insertion(+), 1 deletion(-)
vagrant@ubuntu:~/Documents/dev/mc-test$ git switch stem2
Switched to branch 'stem2'
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git commit -m "rebase test u"
[stem2 61363f6] rebase test u
  1 rebase test u
  2
  3 # Please enter the commit message for your changes. Lines starting
  4 # with '#' will be ignored, and an empty message aborts the commit.
  5 #
  6 # interactive rebase in progress; onto bb37a81
  7 # Last command done (1 command done):
  8 #    pick 61363f6 rebase test u
  9 # No commands remaining.
 10 # You are currently rebasing branch 'stem2' on 'bb37a81'.
 11 #
 12 # Changes to be committed:
 13 #   modified:   test.txt
 14 #

 ~
"~/Documents/dev/mc-test/.git/COMMIT_EDITMSG" 14L, 406B                                                                     1,1           All
  1 rebase test u
 1 file changed, 1 insertion(+), 1 deletion(-)
vagrant@ubuntu:~/Documents/dev/mc-test$ git rebase main
fatal: invalid upstream 'main'
vagrant@ubuntu:~/Documents/dev/mc-test$ git rebase master
Auto-merging test.txt
CONFLICT (content): Merge conflict in test.txt
error: could not apply 61363f6... rebase test u
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
hint: You can instead skip this commit: run "git rebase --skip".
hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
Could not apply 61363f6... rebase test u
vagrant@ubuntu:~/Documents/dev/mc-test$ cat test.txt
<<<<<<< HEAD
t
=======
u
>>>>>>> 61363f6 (rebase test u)
vagrant@ubuntu:~/Documents/dev/mc-test$ vi test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ cat test.txt
u from t
vagrant@ubuntu:~/Documents/dev/mc-test$ git status
interactive rebase in progress; onto bb37a81
Last command done (1 command done):
   pick 61363f6 rebase test u
No commands remaining.
You are currently rebasing branch 'stem2' on 'bb37a81'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git restore --staged <file>..." to unstage)
  (use "git add <file>..." to mark resolution)
	both modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")
vagrant@ubuntu:~/Documents/dev/mc-test$ git add test.txt
vagrant@ubuntu:~/Documents/dev/mc-test$ git rebase --continue
[detached HEAD 32585f2] rebase test u
 1 file changed, 1 insertion(+), 1 deletion(-)
Successfully rebased and updated refs/heads/stem2.
