# Bandit Level 18 -> Level 19:

As the .bashrc is modified so that we get logged out instantly, we use a command with our ssh login which executes before we get logged out, to read the file.

```sh
user@localhost:~$ ssh bandit18@bandit.labs.overthewire.org -p 2220 'cat readme'
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```
