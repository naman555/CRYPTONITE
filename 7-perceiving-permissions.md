# Changing File Ownership
>In this challenge, we learn about file ownership, starting with the `chown` (change owner) command. We are tasked with changing the owner of the `/flag` file to our current user so that we can read it.

## Solve:
- Used the `chown` command to change the ownership of `/flag` from `root` to `hacker`.
- Used the `cat` command to read the contents of the `/flag` file and retrieve the flag.

```bash
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{ksxD_SbDoBz33efGe4jAo5WdX0k.QXxEjN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{ksxD_SbDoBz33efGe4jAo5WdX0k.QXxEjN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `chown` command to change file ownership.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# Groups and Files
>In this challenge, we learn how to change group ownership using the `chgrp` command. The flag is readable by the group that owns it, and we are granted the ability to invoke `chgrp` as the `hacker` user to gain access.

## Solve:
- Used the `chgrp` command to change the group ownership of `/flag` to the `hacker` group.
- Used the `cat` command to read the `/flag` file, which we now had group read access to.

```bash
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{QOb3ClG9zJnX3BhZ-W2tf_zylsL.QXxcjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{QOb3ClG9zJnX3BhZ-W2tf_zylsL.QXxcjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `chgrp` command to change group ownership of a file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# Fun with Group Names
>In this challenge, we are not explicitly told which group our user belongs to. We must first identify our primary group and then use `chgrp` to grant ourselves access to the `/flag` file.

## Solve:
- Used the `id` command to identify our current user and primary group (`grp32680`).
- Used `chgrp` to change the group ownership of `/flag` to `grp32680`.
- Used `cat` to read the flag.

```bash
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp11952) groups=1000(grp11952)
hacker@permissions~fun-with-groups-names:~$ chgrp grp11952 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{YNR5edCpG5CGLqn6U3z5c0O_TwO.QXycjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{YNR5edCpG5CGLqn6U3z5c0O_TwO.QXycjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `id` command to discover user and group identifiers.
- Using `chgrp` to discover group names.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# Changing Permissions
>In this challenge, we learn how to change file permissions using the `chmod` command. The basic format is `chmod [OPTIONS] MODE FILE`, where the mode can be specified numerically or symbolically to overwrite or modify existing permissions.

## Solve:
- Used the `chmod 644 /flag` command to grant read permissions to the owner, group, and others.
- Used `cat` to read the now-accessible `/flag` file.

```bash
hacker@permissions~changing-permissions:~$ chmod 644 /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{0d-KLyHeN3Emvf_XgTLhRdQFoje.QXzcjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{0d-KLyHeN3Emvf_XgTLhRdQFoje.QXzcjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Changing file permissions using `chmod`.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# Executable Files
>In this challenge, we learn how to make files executable. Linux will only execute a program if the user has execute permissions for that specific file. We are tasked with making the `/challenge/run` program executable to retrieve the flag.

## Solve:
- Used `chmod +x /challenge/run` to add execute permissions for all users.
- Executed the `/challenge/run` program to receive the flag.

```bash
hacker@permissions~executable-files:~$ chmod +x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{MU-FedW-CwZEPw_1u70My-30W01.QXyEjN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{MU-FedW-CwZEPw_1u70My-30W01.QXyEjN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `chmod +x` to make a file executable.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# Permission Tweaking Practice
>In this challenge, we practice our understanding of `chmod` by iteratively changing the permissions of `/challenge/pwn` across eight rounds. Successfully completing the rounds grants us the ability to modify and read the `/flag` file.

## Solve:
- Followed the challenge prompts, using symbolic `chmod` modes to match the required permissions for `/challenge/pwn` in each round.
- After completing all 8 rounds, used `chmod u+r /flag` to grant ourselves read access.
- Used `cat` to read the flag.

```bash
hacker@permissions~permission-tweaking-practice:~$ chmod u-r,o-r /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": -w-r-----
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---r-----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-w /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": ---r-----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---r-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+x /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": ---r-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xr-x---
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+rx /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r-xr-x---
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-x--x---
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g-r /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": r-x--x---
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xrwxrw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+rw,o+rw /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": r-xrwxrw-
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r-xrwxr--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o-w /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": r-xrwxr--
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ---rwxr--
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+rw /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~permission-tweaking-practice:~$ cat /challenge/pwn
hacker@permissions~permission-tweaking-practice:~$ chmod u+rw /flag
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{EiDD2Vi67fsBhqhR0aV-TZxdR6J.QXwEjN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{EiDD2Vi67fsBhqhR0aV-TZxdR6J.QXwEjN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using chmod to grant different permissions

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# Permissions Setting Practice
>In this challenge, we learn how to use `chmod` to completely overwrite existing permissions using the `=` operator, often combined with comma-chaining to modify multiple entities at once.

## Solve:
- Followed the challenge prompts, using `=` and `,` to set exact permissions for `/challenge/pwn` in each round (e.g., `u=r,g=rwx,o=x`).
- After completing all 8 rounds, used `chmod u+r /flag` to grant read access.
- Used `cat` to read the flag.

```bash
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxr---wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,o=wx /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": -wxr---wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -w-r--r--
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=r,o=r /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": -w-r--r--
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --xr--rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g=r,o=rwx /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": --xr--rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r------wx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g-r,o=wx /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": r------wx
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ---rw----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u-r,g=rw,o-wx /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": ---rw----
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-r-xrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rx,o=rw /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": -w-r-xrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r---wx-w-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=wx,o=w /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": r---wx-w-
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --x---r-x
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g-wx,o=rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u+rw /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{836dITaVikLEb9WmUcF9oQESpPM.QXzETO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{836dITaVikLEb9WmUcF9oQESpPM.QXzETO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `=` operator with `chmod` to completely overwrite existing permissions.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)

---

# The SUID Bit
>In this challenge, we learn about the SUID (Set User ID) bit. When set on an executable, it allows the program to run with the permissions of the file's owner (often `root`), rather than the user executing it. We are tasked with setting the SUID bit on `/challenge/getroot` to spawn a root shell.

## Solve:
- Used `chmod u+s /challenge/getroot` to set the SUID bit on the program.
- Verified the change using `ls -l`, noting the `s` in the user execute position (`-rwsr-xr-x`).
- Executed `/challenge/getroot` to spawn a root shell.
- Used `cat /flag` within the root shell to read the flag.

```bash
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:/home/hacker# cat /flag
pwn.college{sKimHta4lBwPa2VrZJ7A_Qo8mds.QXzEjN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{sKimHta4lBwPa2VrZJ7A_Qo8mds.QXzEjN0wCN2AzNwIzW}
```

## Concepts Learnt
- How to set the SUID bit using `chmod u+s`.

## References
- [pwn.college](https://pwn.college/linux-luminarium/permissions/)
