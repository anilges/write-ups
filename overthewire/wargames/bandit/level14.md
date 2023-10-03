# Bandit Level 14 -> Level 15:

With `nc` we can send data to a specific IP and port over udp/tcp. Also we use a "here string" in bash to pass the string to the standard input of our command on the left.By using this, we don't need to run a subshell.

```sh
bandit14@bandit:~$ nc localhost 30000 <<< fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```
