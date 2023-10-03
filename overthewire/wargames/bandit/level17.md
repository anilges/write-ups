# Bandit Level 17 -> Level 18:

As we received an ssh private key from the last level, we copy it to our local machine and set the correct permissions `chmod 600 key`, so that we can connect over ssh with that key.
For this level we use the `diff` command to find the only changed line in the given files to receive the password.

```sh
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< glZreTEH1V3cGKL6g4conYqZqaEj0mte
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
```

