# Matching with *
>In this challenge, we learn about using the `*` wildcard pattern to match directory names. We navigate to the `/challenge` directory using a glob pattern and executing the run script to retrieve the flag.

## Solve:
- Used the `cd /ch*` command to navigate to the `/challenge` directory, utilised the `*` wildcard to match the remainder of the directory name.
- Executed the `/challenge/run` script, which verified the working directory and output the flag.

```
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{Y8fVIUSF1uFfamIK8hGJpvmVBn8.QXxIDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{Y8fVIUSF1uFfamIK8hGJpvmVBn8.QXxIDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `*` wildcard to match zero or more characters in a path.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Matching with ?
>In this challenge, we learn about using the `?` wildcard to match exactly one character in a path. We are tasked with navigating to the `/challenge` directory using a pattern with `?` and executing the run script.

## Solve:
- Used the `cd /?ha??enge` command to navigate to the `/challenge` directory, utilising the `?` wildcard to match single characters in the directory name.
- Executed the `./run` script, which verified the working directory and output the flag.

```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{I3JP4c7GVhs8PgpiItVnTAY9GN1.QXyIDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{I3JP4c7GVhs8PgpiItVnTAY9GN1.QXyIDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `?` wildcard to match exactly one character in a filename or path.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Matching with []
>In this challenge, we learn about using the `[]` wildcard to match any single character within the specified brackets. We are tasked with passing a specific file matching this pattern to the challenge script.

## Solve:
- Navigated to the `/challenge/files/` directory and listed its contents using `ls`.
- Executed the `/challenge/run` command with the argument `file_[bash]`, using the `[]` glob to match a file ending in 'b', 'a', 's', or 'h', which satisfied the challenge conditions and returned the flag.

```
hacker@globbing~matching-with-:~$ cd /challenge/files/
hacker@globbing~matching-with-:/challenge/files$ ls
file_a  file_c  file_e  file_g  file_i  file_k  file_m  file_o  file_q  file_s  file_u  file_w  file_y
file_b  file_d  file_f  file_h  file_j  file_l  file_n  file_p  file_r  file_t  file_v  file_x  file_z
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{881Jpsw8SIJ1q1_4opr6qtTG2Up.QXzIDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{881Jpsw8SIJ1q1_4opr6qtTG2Up.QXzIDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using character classes `[]` in globs to match any single character from a specified set.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Matching paths with []
>In this challenge, we learn about using the `[]` wildcard to match specific characters in a filename. We are tasked with passing a file matching this pattern to the challenge executable.

## Solve:
- Executed the `/challenge/run` command with the argument `/challenge/files/file_[bash]`.
- The `[]` glob successfully matched the target file, satisfying the challenge conditions and outputting the flag.

```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{EaKfGrR_CPVtJhddUz7C9Ei5eKO.QX0IDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{EaKfGrR_CPVtJhddUz7C9Ei5eKO.QX0IDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using comma-separated values inside `[]` to explicitly define a set of characters to match.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Multiple globs
>In this challenge, we learn about using multiple wildcards (`*`) in a single glob pattern to match filenames containing specific characters. We are tasked with passing all files containing the letter 'p' to the challenge executable.

## Solve:
- Listed the contents of the `/challenge/files/` directory using `ls` to see the available files.
- Navigated to the directory and executed the `../run` command with the `*p*` glob pattern, which expanded to all filenames containing the letter 'p', successfully satisfying the challenge and returning the flag.

```
hacker@globbing~multiple-globs:~$ ls /challenge/files/
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~multiple-globs:~$ cd /challenge/files/
hacker@globbing~multiple-globs:/challenge/files$ ../run *p*
You got it! Here is your flag!
pwn.college{sHZFxQwTW06zyoKaNP4Zz_tYjIz.0lM3kjNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{sHZFxQwTW06zyoKaNP4Zz_tYjIz.0lM3kjNxwCN2AzNwIzW}
```

## Concepts Learnt
- Using multiple `*` wildcards in a single pattern to match characters anywhere in a filename.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Mixing globs
>In this challenge, we learn about combining different globbing techniques, such as character classes `[]` and wildcards `*`, to match specific filenames. We are tasked with passing a file that starts with 'c', 'e', or 'p' to the challenge executable.

## Solve:
- Navigated to the `/challenge/files/` directory.
- Executed the `../run` command with the `[cep]*` glob pattern, which matched any file starting with 'c', 'e', or 'p', satisfying the challenge conditions and outputting the flag.

```
hacker@globbing~mixing-globs:~$ cd /challenge/files/
hacker@globbing~mixing-globs:/challenge/files$ ../run [cep]*
You got it! Here is your flag!
pwn.college{8LeQYkuSAGiXYeijBoN9NKb2CtB.QX1IDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{8LeQYkuSAGiXYeijBoN9NKb2CtB.QX1IDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Combining character classes `[]` with wildcards `*` to create more precise glob patterns.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Exclusionary globbing
>In this challenge, we learn about using exclusionary globbing with the `!` or `^` character inside brackets `[]` to match any character *except* those specified. We are tasked with passing a file that does not start with 'p', 'w', or 'n' to the challenge executable.

## Solve:
- Navigated to the `/challenge/files/` directory.
- Executed the `../run` command with the `[!pwn]*` glob pattern, which expanded to files that do not start with 'p', 'w', or 'n', successfully satisfying the challenge and returning the flag.

```
hacker@globbing~exclusionary-globbing:/challenge/files$ cd /challenge/files/
hacker@globbing~exclusionary-globbing:/challenge/files$ ../run [!pwn]*
You got it! Here is your flag!
pwn.college{U2_RazfMdF-Mm4zEX_n5Nf-aZiK.QX2IDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{U2_RazfMdF-Mm4zEX_n5Nf-aZiK.QX2IDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `!` inside `[]` to negate a character class and match anything except the specified characters.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Tab completion
>In this challenge, we learn about utilising tab completion in the shell to quickly and accurately type out long file paths or commands. We are tasked with reading a specific file in the `/challenge/` directory.

## Solve:
- Used the `cat` command and leveraged tab completion to autocomplete the filename `/challenge/pwncollege`.
- Read the contents of the file to retrieve the flag.

```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege
pwn.college{gdXMgCZ-1IxsmAxUJ53V--KgbGz.0FN0EzNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{gdXMgCZ-1IxsmAxUJ53V--KgbGz.0FN0EzNxwCN2AzNwIzW}
```

## Concepts Learnt
- Using the `Tab` key to autocomplete file paths and commands in the shell.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Multiple options for tab completion
>In this challenge, we learn how the shell handles tab completion when multiple files share the same prefix. We are tasked with identifying the correct file among several options and reading its contents.

## Solve:
- Attempted to use tab completion on `/challenge/files/pwn`, which displayed multiple matching files since the prefix was not unique.
- Extended the prefix to `/challenge/files/pwncollege-flag` to uniquely identify the target file.
- Used the `cat` command to read the contents of the correctly autocompleted file and retrieve the flag.

```
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwn
pwn                    pwn-the-planet         pwncollege-flag        pwncollege-flyswatter
pwn-college            pwncollege-family      pwncollege-flamingo    pwncollege-hacking
hacker@globbing~multiple-options-for-tab-completion:~$ cat /challenge/files/pwncollege-flag
pwn.college{cMRDa8vy6bKeq5MH4mQbk2XfFCL.0lN0EzNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{cMRDa8vy6bKeq5MH4mQbk2XfFCL.0lN0EzNxwCN2AzNwIzW}
```

## Concepts Learnt
- How the shell responds to tab completion when a prefix matches multiple files (displaying options).

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)

---

# Tab completion on commands
>In this challenge, we learn about using tab completion for commands, not just file paths. We are tasked with finding and executing a specific challenge binary whose name starts with a known prefix.

## Solve:
- Typed the prefix `pwncollege-` and used tab completion to autocomplete the full command name (e.g., `pwncollege-30538`).
- Executed the autocompleted command, which verified the action and output the flag.

```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-30538
Correct! Here is your flag:
pwn.college{ka61-xB5NFMMX3XY53gTYfT6BK_.0VN0EzNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{ka61-xB5NFMMX3XY53gTYfT6BK_.0VN0EzNxwCN2AzNwIzW}
```

## Concepts Learnt
- Using tab completion to autocomplete executable command names in the `$PATH` or current directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/globbing/)
