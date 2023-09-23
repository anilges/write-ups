# Bandit Level 6 -> Level 7:

Here we use `find` once more with a few flags to find exactly the described file.
Also we redirect stderr to `/dev/null`.

```sh
bandit6@bandit:~$ cat `find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
