# cat: not the pet, but the command!
>In this challenge, we learn about reading the contents of files using the `cat` command. We are tasked with listing the files in our current directory and then reading the contents of the `flag` file to retrieve the flag.

## Solve:
- Used the `ls` command to list the files in the current directory.
- Used the `cat` command to read the contents of the `flag` file and retrieve the flag.

```
hacker@commands~cat-not-the-pet-but-the-command:~$ ls
a  flag
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{YoiabAKoyy2HODJzb3zlOe5m41R.QXxcTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{YoiabAKoyy2HODJzb3zlOe5m41R.QXxcTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `ls` to list directory contents.
- Using `cat` to read and display the contents of a file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# catting absolute paths
>In this challenge, we learn about reading files using absolute paths. We are tasked with using the `cat` command to read a file located at the root directory (`/flag`) without needing to change our current working directory.

## Solve:
- Used the `cat` command with the absolute path `/flag` to read the file and retrieve the flag.

```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{k6DAdb12q9ZkA06_0A1LF1MIfcX.QX5ETO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{k6DAdb12q9ZkA06_0A1LF1MIfcX.QX5ETO0wCN2AzNwIzW}
```

## Concepts Learnt
- Reading files using absolute paths.
- Using `cat` with absolute file paths to access files from anywhere in the filesystem.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# more catting practice
>In this challenge, we practice reading files from the filesystem using absolute paths. We are given the exact path to a hidden flag file and must read it using `cat` without changing directories.

## Solve:
- Read the challenge prompt to find the absolute path of the flag file.
- Used the `cat` command with the absolute path `/usr/include/asm-generic/flag` to read the file and retrieve the flag.

```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /usr/include/asm-generic/flag. Go cat it out without using cd!
hacker@commands~more-catting-practice:~$ cat /usr/include/asm-generic/flag
pwn.college{4Nxu2n1aUOeT-bJIH8OA8C2v49a.QXwITO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{4Nxu2n1aUOeT-bJIH8OA8C2v49a.QXwITO0wCN2AzNwIzW}
```

## Concepts Learnt
- Reading files using `cat`

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# grepping for a needle in a haystack
>In this challenge, we learn about searching for specific text within a file using the `grep` command. We are tasked with finding the flag hidden somewhere inside a large text file.

## Solve:
- Used the `cat` command to output the contents of `/challenge/data.txt`.
- Piped the output into the `grep` command with the search term `pwn.college` to filter and find the flag.

```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ cat /challenge/data.txt | grep pwn.college
pwn.college{4fpUW8t9kkjjnjfT0iOcq5qIiFU.QX3EDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{4fpUW8t9kkjjnjfT0iOcq5qIiFU.QX3EDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `grep` to search for specific patterns or strings within text.
- Using the pipe (`|`) operator to pass the output of one command as input to another.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# comparing files
>In this challenge, we learn about comparing the contents of two files using the `diff` command. We are tasked with finding the flag by identifying the differences between a file containing only decoys and a file containing the real flag.

## Solve:
- Used the `diff` command to compare `/challenge/decoys_only.txt` and `/challenge/decoys_and_real.txt`.
- Identified the added line in the output, which contained the flag.

```
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
40a41
> pwn.college{47dBu-3udfFfdKO60YT5z5ynZdV.01MwMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{47dBu-3udfFfdKO60YT5z5ynZdV.01MwMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using `diff` to compare two files line by line.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# listing files
>In this challenge, we learn about listing the contents of directories to find hidden or renamed files. We are tasked with finding the challenge executable, which has been renamed, and running it to get the flag.

## Solve:
- Used the `ls` command to list the contents of the `/challenge/` directory.
- Identified the renamed executable file `22953-renamed-run-13674`.
- Executed the renamed file using its absolute path to retrieve the flag.

```
hacker@commands~listing-files:~$ ls /challenge/
22953-renamed-run-13674  Dockerfile
hacker@commands~listing-files:~$ /challenge/22953-renamed-run-13674
Yahaha, you found me! Here is your flag:
pwn.college{EJmqD9GkWH2OdQs8JAmQEzd4kPs.QX4IDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{EJmqD9GkWH2OdQs8JAmQEzd4kPs.QX4IDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `ls` to discover files in a directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# touching files
>In this challenge, we learn about creating empty files using the `touch` command. We are tasked with creating specific files in the `/tmp` directory to satisfy the conditions of the challenge program.

## Solve:
- Used the `touch` command to create two empty files named `pwn` and `college` in the `/tmp` directory.
- Executed the `/challenge/run` program

```
hacker@commands~touching-files:~$ touch /tmp/pwn /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{EchFCnIoS45kYVX8ch5cU6F5vzN.QXwMDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{EchFCnIoS45kYVX8ch5cU6F5vzN.QXwMDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `touch` to create new, empty files.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# removing files
>In this challenge, we learn about deleting files using the `rm` command. We are tasked with removing a specific file from our current directory to pass the challenge's verification step.

## Solve:
- Used the `ls` command to identify the file that needed to be removed (`delete_me`).
- Used the `rm` command to delete the `delete_me` file.
- Ran the `/challenge/check` program to verify the removal and retrieve the flag.

```
hacker@commands~removing-files:~$ ls
a  delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{IQMLJVxUw-jT0K_0-8qhAQpn_RU.QX2kDM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{IQMLJVxUw-jT0K_0-8qhAQpn_RU.QX2kDM1wCN2AzNwIzW}
```

## Concepts Learnt
- Using `rm` to delete files from the filesystem.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# moving files
>In this challenge, we learn about moving or renaming files using the `mv` command. We are tasked with moving the flag file to a specific location and filename to satisfy the challenge requirements.

## Solve:
- Used the `mv` command to move the `/flag` file to `/tmp/hack-the-planet`.
- Ran the `/challenge/check` program to verify the move operation and retrieve the flag.

```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/run
bash: /challenge/run: No such file or directory
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{EoZbe23Ob2JCwmBXqhn3BBHsNZN.0VOxEzNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{EoZbe23Ob2JCwmBXqhn3BBHsNZN.0VOxEzNxwCN2AzNwIzW}
```

## Concepts Learnt
- Using `mv` to move and rename files to different directories.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# copying files
>In this challenge, we learn about duplicating files using the `cp` command. We are tasked with creating a copy of the flag file in a specific location to satisfy the challenge requirements.

## Solve:
- Used the `cp` command to copy the `/flag` file to `/tmp/hack-the-planet`.
- Ran the `/challenge/check` program to verify the copy operation and retrieve the flag.

```
hacker@commands~copying-files:~$ cp /flag /tmp/hack-the-planet
Correct! Performing 'cp /flag /tmp/hack-the-planet'.
hacker@commands~copying-files:~$ /challenge/check
Congrats! You successfully copied the flag to /tmp/hack-the-planet! Here it is:
pwn.college{EakZ8drlACWqWNC9DonLbDtD21T.0lNxQTMywCN2AzNwIzW}
```

## Flag
```
pwn.college{EakZ8drlACWqWNC9DonLbDtD21T.0lNxQTMywCN2AzNwIzW}
```

## Concepts Learnt
- Using `cp` to duplicate files.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# hidden files
>In this challenge, we learn about hidden files in Linux, which are files whose names begin with a dot (`.`). We are tasked with finding a hidden flag file in the root directory and reading its contents.

## Solve:
- Used the `ls -a` command to list all files, including hidden ones, in the root directory (`/`).
- Identified the hidden flag file named `.flag-8141152136134`.
- Used the `cat` command to read the contents of the hidden file and retrieve the flag.

```
hacker@commands~hidden-files:~$ ls -a /
.   .dockerenv           bin   challenge  etc   lib    media  nix  proc  run   srv  tmp  var
..  .flag-8141152136134  boot  dev        home  lib64  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-8141152136134
pwn.college{QMziYA2qY-NajdRPbMpMI3CiZUn.QXwUDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{QMziYA2qY-NajdRPbMpMI3CiZUn.QXwUDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Understanding hidden files in Linux (files starting with `.`).
- Using the `-a` flag with `ls` to view hidden files.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# An Epic Filesystem Quest
>In this challenge, we use the various tools like `ls`, `cat` and `cd` to navigate through directories and hidden files to get the final flag.

## Solve:
- Read the initial clue in `/TRACE` to find the next directory.
- Used `ls -a` to find hidden clues and avoided `cd`ing into trapped directories by using absolute paths with `cat`.
- Used `cd` only when a clue required entering a directory to unlock a delayed file.
- Read the final hidden clue `.WHISPER` to retrieve the flag.

```
hacker@commands~an-epic-filesystem-quest:~$ ls /
TRACE  bin  boot  challenge  dev  etc  flag  home  lib  lib64  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~an-epic-filesystem-quest:~$ cat /TRACE
Lucky listing!
The next clue is in: /usr/share/perl/5.38.2/TAP/Parser/Result

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:~$ ls -a /usr/share/perl/5.38.2/TAP/Parser/Result
.  ..  Bailout.pm  Comment.pm  POINTER-TRAPPED  Plan.pm  Pragma.pm  Test.pm  Unknown.pm  Version.pm  YAML.pm
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/perl/5.38.2/TAP/Parser/Result/POINTER-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/perl/5.38.2/Test2/API
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/perl/5.38.2/Test2/API/
Breakage.pm         Instance.pm         InterceptResult.pm  Stack.pm
Context.pm          InterceptResult/    MESSAGE
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/perl/5.38.2/Test2/API/MESSAGE
Tubular find!
The next clue is in: /usr/share/perl/5.38.2/CPAN/Meta

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/perl/5.38.2/CPAN/Meta/
Converter.pm     History/         Merge.pm         Requirements.pm  TIP-TRAPPED      YAML.pm
Feature.pm       History.pm       Prereqs.pm       Spec.pm          Validator.pm
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/perl/5.38.2/CPAN/Meta/TIP-TRAPPED
Yahaha, you found me!
The next clue is in: /usr/share/locale/af

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/locale/af/
.BRIEF   LC_TIME/
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/locale/af/.BRIEF
Great sleuthing!
The next clue is in: /usr/share/doc/libpam-modules/examples
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/doc/libpam-modules/examples/
CLUE          upperLOWER.c
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/doc/libpam-modules/examples/
CLUE          upperLOWER.c
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/doc/libpam-modules/examples/CLUE
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/pygments

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/lib/python3/dist-packages/pygments/
.INFO         __pycache__/  filter.py     formatters/   modeline.py   scanner.py    styles/       util.py
__init__.py   cmdline.py    filters/      lexer.py      plugin.py     sphinxext.py  token.py
__main__.py   console.py    formatter.py  lexers/       regexopt.py   style.py      unistring.py
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/lib/python3/dist-packages/pygments/.INFO
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/pygments/filters

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/lib/python3/dist-packages/pygments/filters
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/pygments/filters$ ls -a
.  ..  BLUEPRINT  __init__.py  __pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/pygments/filters$ cat BLUEPRINT
Congratulations, you found the clue!
The next clue is in: /usr/share/locale/ko/LC_MESSAGES

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/pygments/filters$ cat /usr/share/locale/ko/LC_MESSAGES/
.WHISPER          apt.mo            dpkg.mo           libapt-pkg6.0.mo
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/pygments/filters$ cat /usr/share/locale/ko/LC_MESSAGES/.WHISPER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{wQN1-wyPjkz6hd-PLhqZWgFq3iU.QX5IDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{wQN1-wyPjkz6hd-PLhqZWgFq3iU.QX5IDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Combining previously used tools to navigate through the filesystem

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# making directories
>In this challenge, we learn about creating new directories using the `mkdir` command. We are tasked with creating a specific directory structure and creating a file in it to satisfy the challenge program.

## Solve:
- Used the `mkdir` command to create a new directory named `pwn` inside `/tmp`.
- Used the `touch` command to create an empty file named `college` inside the newly created `/tmp/pwn` directory.
- Executed the `/challenge/run` program to verify the structure and retrieve the flag.

```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{gEelJZPrEf7pZS52jd24W3xoY0_.QXxMDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{gEelJZPrEf7pZS52jd24W3xoY0_.QXxMDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `mkdir` to create new directories.
- Combining directory creation with file creation to build filesystem structures.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# finding files
>In this challenge, we learn about searching the filesystem for files matching specific criteria using the `find` command. We are tasked with locating a file named `flag` hidden somewhere in the system.

## Solve:
- Used the `find / -name flag` command to search the entire filesystem for files named `flag`.
- Used the `cat` command to read the contents of the found file and retrieve the flag.

```
hacker@commands~finding-files:~$ find / -name flag
find: ‘/etc/ssl/private’: Permission denied
/usr/lib/gcc/x86_64-linux-gnu/flag
/usr/lib/python3/dist-packages/pwnlib/flag
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/root’: Permission denied
^C
hacker@commands~finding-files:~$ cat /usr/lib/gcc/x86_64-linux-gnu/flag
pwn.college{UVM81y-4SPX_S8crgYGnvovazUN.QXyMDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{UVM81y-4SPX_S8crgYGnvovazUN.QXyMDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `find` to search for files by name across the filesystem.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)

---

# linking files
>In this challenge, we learn about creating symbolic links to files using the `ln` command. We are tasked with creating a symbolic link in our home directory that points to the root flag file.

## Solve:
- Used the `ln -sf` command to create a symbolic link named `not-the-flag` in the home directory that points to `/flag`.
- Executed the `/challenge/catflag` program, which read the symbolic link and provided the flag.

```
hacker@commands~linking-files:~$ ln -sf /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{cz0mnU1VUhOZE-xrTfzkmkqiXlM.QX5ETN1wCN2AzNwIzW}
```

## Flag
```
pwn.college{cz0mnU1VUhOZE-xrTfzkmkqiXlM.QX5ETN1wCN2AzNwIzW}
```

## Concepts Learnt
- Using `ln -s` to create symbolic links.
- Using the `-f` flag to force the creation of a link, overwriting existing files if necessary.

## References
- [pwn.college](https://pwn.college/linux-luminarium/commands/)
