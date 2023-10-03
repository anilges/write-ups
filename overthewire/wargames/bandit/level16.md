# Bandit Level 16 -> Level 17:

First we use `nmap localhost -p 31000-32000` to scan the machine for the given ports. We can see that 5 are open. Now we just test the command from the previous level and see that we receive a ssh private key with port 31790.

```sh
bandit16@bandit:~$ nmap localhost -p 31000-32000
Starting Nmap 7.80 ( https://nmap.org ) at 2023-10-03 10:35 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00019s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.06 seconds
bandit16@bandit:~$ openssl s_client -connect localhost:31790 -ign_eof <<< JQttfApK4SeyHwDlI9SXGR50qclOAil1
Correct!
```

