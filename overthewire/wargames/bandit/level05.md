# Bandit Level 5 -> Level 6:

Here we can use `find . -ls` to show us all files recursively with more details, including the file size. We pipe that to `grep 1033` to search for the given file size in bytes. Now that we found the file we can read it with `head -1` to only get the first line.

```sh
bandit5@bandit:~$ find . -ls | grep 1033
   292565      4 -rw-r-----   1 root     bandit5      1033 Apr 23 18:04 ./inhere/maybehere07/.file2
bandit5@bandit:~$ head -1 ./inhere/maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```
