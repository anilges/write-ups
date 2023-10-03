# Bandit Level 13 -> Level 14:

In this level we have to use the given private ssh key to login with as user bandit14. With `ssh -i` we can use a private key as the login and don't need the password.

```sh
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```
