# Bandit Level 20 -> Level 21:

For this level we use `screen` as our terminal multiplexer. In our first screen, we use `nc` to listen to incoming connections on port 9001:

```sh
bandit20@bandit:~$ nc -lvnp 9001
Listening on 0.0.0.0 9001
```

On the second screen we use `./suconnect 9001` to make a connection to that port on localhost.

Then on our listener screen, we can send the current password to receive the next one:

```sh
bandit20@bandit:~$ nc -lvnp 9001
Listening on 0.0.0.0 9001
Connection received on 127.0.0.1 43530
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```
