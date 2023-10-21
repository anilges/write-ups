# Bandit Level 28 -> Level 29:

Here we need to clone the repo and then search a bit more for the password.

```sh
bandit28@bandit:~$ mkdir /tmp/gitfiles28
bandit28@bandit:~$ cd /tmp/gitfiles28
bandit28@bandit:/tmp/gitfiles28$ git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
Cloning into 'repo'...
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit28-git@localhost's password:
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
bandit28@bandit:/tmp/gitfiles28$ ls
repo
bandit28@bandit:/tmp/gitfiles28$ cd repo/
bandit28@bandit:/tmp/gitfiles28/repo$ ls
README.md
bandit28@bandit:/tmp/gitfiles28/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```

We look at the commit history and find a suspicious commit message "fix info leak", so we revert back to the state before the fix and find the password in the README file.

```sh
bandit28@bandit:/tmp/gitfiles28/repo$ git log
commit 14f754b3ba6531a2b89df6ccae6446e8969a41f3 (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    fix info leak

commit f08b9cc63fa1a4602fb065257633c2dae6e5651b
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    add missing data

commit a645bcc508c63f081234911d2f631f87cf469258
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Oct 5 06:19:41 2023 +0000

    initial commit of README.md
bandit28@bandit:/tmp/gitfiles28/repo$ git reset f08b9cc63fa1a4602fb065257633c2dae6e5651b
Unstaged changes after reset:
M       README.md
bandit28@bandit:/tmp/gitfiles28/repo$ git status
On branch master
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
bandit28@bandit:/tmp/gitfiles28/repo$ git restore README.md
bandit28@bandit:/tmp/gitfiles28/repo$ cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
```
