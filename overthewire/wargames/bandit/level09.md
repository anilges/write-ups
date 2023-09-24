# Bandit Level 9 -> Level 10:

Here we use `strings` to get the human-readable strings and then search for the lines with several preceding "=" characters by using grep with a extended regular expression.

```sh
bandit9@bandit:~$ strings data.txt | grep -E '^=='
========== password
========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
