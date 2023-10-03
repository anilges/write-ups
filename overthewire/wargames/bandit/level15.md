# Bandit Level 15 -> Level 16:

Here we use `openssl s_client` to connect over SSL/TLS to the given host and port and also give the `-ign_eof` flag to receive the answer.

```sh
bandit15@bandit:~$ openssl s_client -connect localhost:30001 -ign_eof <<< jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```
