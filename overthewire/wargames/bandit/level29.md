# Bandit Level 29 -> Level 30:

Again, we get a git repo to search for the password.

```sh
bandit29@bandit:/tmp/gitrepo29$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
Cloning into 'repo'...
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit29-git@localhost's password:
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (16/16), done.
Resolving deltas: 100% (2/2), done.
bandit29@bandit:/tmp/gitrepo29$ ls
repo
bandit29@bandit:/tmp/gitrepo29$ cd repo/
bandit29@bandit:/tmp/gitrepo29/repo$ ls
README.md
bandit29@bandit:/tmp/gitrepo29/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>
```

This time again we can't directly find the password in the README file, but we get a hint, that the password is not used in production. We then look for other branches and find the `dev` branch with looks promising, because if the password is not in production, it is probably in the development branch.

```sh
bandit29@bandit:/tmp/gitrepo29/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/gitrepo29/repo$ git switch dev
Branch 'dev' set up to track remote branch 'dev' from 'origin'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/gitrepo29/repo$ ls
code  README.md
bandit29@bandit:/tmp/gitrepo29/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
```

And here we find the password.
