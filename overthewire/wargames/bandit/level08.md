# Bandit Level 8 -> Level 9:

For this we can use `uniq -u` to get the line that only occures once. But first we sort the file with `sort`, as `uniq` only works on sorted files.

```sh
bandit8@bandit:~$ sort data.txt | uniq -u
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
