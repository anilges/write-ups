# Level 1:

Here you have to read the file `-`. But as you will see `cat -` will not work. `man cat` tells us why: "With no FILE, or when FILE is -, read standard input.". So we need to give `cat` the full relative path to this file. From the current location this is `./-`.

```sh
bandit1@bandit:~$ find .
.
./-
./.profile
./.bashrc
./.bash_logout
bandit1@bandit:~$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
