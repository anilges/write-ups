# Level 0:

Here you need to use ssh to login to the given host `bandit.labs.overthewire.org` with the given username `bandit0` as well as the given port `2220` and the given password `bandit0`.
The password for level 1 can then be found by reading the `readme` file, for example with `cat`.

```sh
user@localhost:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
bandit0@bandit.labs.overthewire.org\'s password:
Welcome to OverTheWire!

bandit0@bandit:~$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
