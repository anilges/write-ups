# Bandit Level 11 -> Level 12:

To solve this, we can use the `tr` command, to rotate the letters accordingly. a-z is mapped to n-za-m and A-Z is mapped to N-ZA-M.

```sh
bandit11@bandit:~$ tr 'a-zA-Z' 'n-za-mN-ZA-M' < data.txt
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
