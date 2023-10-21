# Bandit Level 25 -> Level 26:

Here we find the private ssh key of bandit26 in our home directory. This means that we can connect over ssh as this user:

```sh
bandit25@bandit:~$ ssh bandit26@localhost -p 2220 -i bandit26.sshkey

[...]

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
Connection to localhost closed.
```

As we can see, "bandit26" is printed in ascii art, and the connection is closed.
We know from the challenge description, that login shell for bandit26 is not bash. So let's find out what is used:

```sh
bandit25@bandit:~$ grep "bandit26" "/etc/passwd"
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

`/usr/bin/showtext` is the login shell of bandit26, so let's see what is in the file:

```sh
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```

Here we can see that `more ~/text.txt` is executed and after that the shell exits. Now, how can we escape this?
What we need to do is, making sure that the execution of `more` is not finished, so that we can make use of it's feature to open a text editor.
`more` is a pager, which means, that it is used to page through a document, **if it is too big to be shown on the whole screen**. Else it just acts like `cat` meaning it just prints the input to the screen.
So, to achieve this, we need to make our terminal window small, so that only part of the ascii art bandit26 fits on the screen and then we are still in `more`.
As said before, `more` has the ability to open the document in a text editor, in this case `vi`, by pressing `v`.
Now that we are in `vi`, we can either just read the password file:

```
:e /etc/bandit_pass/bandit26
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
```

or additionally even start a bash session:

```
:set shell=/bin/bash
:shell
```
