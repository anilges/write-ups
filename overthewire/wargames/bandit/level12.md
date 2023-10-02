# Bandit Level 12 -> Level 13:

First we make a folder in the /tmp/ directory, so that we have write permissions `mkdir /tmp/apple`. Then we need to revert the hexdump to binary with `xxd -r data.txt > binary`. After that we can use the `file` command to find out the type of file. We have to rename the file to end with `.gz`, as it is a gzip file which needs to have the correct suffix to be unzipped: `mv binary binary.gz`. Then we unzip with `gunzip binary.gz`. Now this has to be done over and over again with different compressing types until the file is of type ASCII text, which holds the password.

```sh
mkdir /tmp/apple && cd "$_"
xxd -r ~/data.txt > binary
file binary
mv binary binary.gz
gunzip binary.gz
bunzip2 binary
mv binary.out binary.gz
gunzip binary.gz
tar -xf binary
tar -xf data5.bin
bunzip2 data6.bin
tar -xf data6.bin.out
mv data8.bin binary1.gz
gunzip binary1.gz
cat binary1

The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```
