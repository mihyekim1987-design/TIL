github에서 branch-practice 라는 새로운 레포 만들기

~/Documents/dev/ 에서 clone하기

branch-practice 디렉토리에 들어간 후 buzz 브랜치만들기

buzz 브랜치에서 fizzbuzz.py 새파일을 만든 후, 작업하기


for i in range(1,15+1):
    if i % 3 == 0:
        print('fizz')
    elif i % 5 == 0:
        print('buzz')
    else:
        print(i)


fizzbuzz.py에 대해 git add, commmit 까지 실시

main branch로 switch 후 buzz 브랜치 merge하기




vagrant@ubuntu:~$ cd Documents/
vagrant@ubuntu:~/Documents$ ls
dev
vagrant@ubuntu:~/Documents$ cd dev
vagrant@ubuntu:~/Documents/dev$ ls
TIL  branch-616  first-repo  markdown.md
vagrant@ubuntu:~/Documents/dev$ git clone https://github.com/kingwangzzang1234/branch-practice.git
Cloning into 'branch-practice'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (4/4), done.
vagrant@ubuntu:~/Documents/dev$ ls
TIL  branch-616  branch-practice  first-repo  markdown.md
vagrant@ubuntu:~/Documents/dev$ cd branch-practice/
vagrant@ubuntu:~/Documents/dev/branch-practice$ ls
LICENSE  README.md
vagrant@ubuntu:~/Documents/dev/branch-practice$ git branch
* main
vagrant@ubuntu:~/Documents/dev/branch-practice$ git branch buzz
vagrant@ubuntu:~/Documents/dev/branch-practice$ git branch
  buzz
* main
vagrant@ubuntu:~/Documents/dev/branch-practice$ git switch buzz
Switched to branch 'buzz'
vagrant@ubuntu:~/Documents/dev/branch-practice$ ls
LICENSE  README.md
vagrant@ubuntu:~/Documents/dev/branch-practice$ touch fizzbuzz.py
vagrant@ubuntu:~/Documents/dev/branch-practice$ ls
LICENSE  README.md  fizzbuzz.py
vagrant@ubuntu:~/Documents/dev/branch-practice$ vi fizzbuzz.py
  1
  2 # Please enter the commit message for your changes. Lines starting
  3 # with '#' will be ignored, and an empty message aborts the commit.
  4 #
  5 # On branch buzz
  6 # Changes to be committed:
  7 #   new file:   fizzbuzz.py
  8 #
~
~
~
~
~
"~/Documents/dev/branch-practice/.git/COMMIT_EDITMSG" 8L, 210B                                                              1,0-1         All
  1 feat: Print fizz or buzz
vagrant@ubuntu:~/Documents/dev/branch-practice$ python fizzbuzz.py
1
2
fizz
4
buzz
fizz
7
8
fizz
buzz
11
fizz
13
14
fizz
vagrant@ubuntu:~/Documents/dev/branch-practice$ cat fizzbuzz.py
for i in range(1, 15+1):
    if i % 3 == 0:
        print('fizz')
    elif i % 5 == 0:
        print('buzz')
    else:
        print(i)
vagrant@ubuntu:~/Documents/dev/branch-practice$ git status
On branch buzz
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	fizzbuzz.py

nothing added to commit but untracked files present (use "git add" to track)
vagrant@ubuntu:~/Documents/dev/branch-practice$ git add fizzbuzz.py
vagrant@ubuntu:~/Documents/dev/branch-practice$ git status
On branch buzz
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	new file:   fizzbuzz.py

vagrant@ubuntu:~/Documents/dev/branch-practice$ git commit
[buzz ef89515] feat: Print fizz or buzz
 1 file changed, 7 insertions(+)
 create mode 100644 fizzbuzz.py
vagrant@ubuntu:~/Documents/dev/branch-practice$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
vagrant@ubuntu:~/Documents/dev/branch-practice$ ls
LICENSE  README.md
vagrant@ubuntu:~/Documents/dev/branch-practice$ git merge buzz
Updating a54f7c6..ef89515
Fast-forward
 fizzbuzz.py | 7 +++++++
 1 file changed, 7 insertions(+)
 create mode 100644 fizzbuzz.py
vagrant@ubuntu:~/Documents/dev/branch-practice$ git branch -D buzz
Deleted branch buzz (was ef89515).
vagrant@ubuntu:~/Documents/dev/branch-practice$ git branch
* main




$ git branch fb
$ vi fizzbuzz.py # i를 j로 바꿈
$ git add fizzbuzz.py
$ git commit -m "fix: Rename variable i to j"
$ git switch fb
$ vi fizzbuzz.py # 15의 배수일때 fizzbuzz 출력
$ git add fizzbuzz.py
$ git commit -m "feat: Print fizzbuzz"
$ vi fizzbuzz.py # i를 k로 바꿈
$ git add fizzbuzz.py
$ git commit -m "fix: Rename variable i to k"
