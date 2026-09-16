# Redirecting output
>In this challenge, we learn about redirecting standard output to a file using the `>` operator. We are tasked with redirecting the output of the `echo` command into a file named `COLLEGE` to satisfy the challenge requirements.

## Solve:
- Used the `echo PWN > COLLEGE` command to redirect the string 'PWN' into a file named `COLLEGE`.
- The challenge verified this redirection and output the flag.

```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{oi7rpq0fL9yQ7qi1CoRubLnrGWv.QX0YTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{oi7rpq0fL9yQ7qi1CoRubLnrGWv.QX0YTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `>` operator to redirect standard output (stdout) to a file, overwriting any existing content.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Redirecting more output
>In this challenge, we learn about redirecting the standard output of challenge to a specific file. We are tasked with running `/challenge/run` and redirecting its stdout to a file named `myflag`.

## Solve:
- Executed `/challenge/run > myflag` to redirect the standard output of the challenge program into the `myflag` file.
- The challenge verified the redirection and placed the flag inside the file.

```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{0CLy36lbEx5mkYMDCig7ggLBDa8.QX1YTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{0CLy36lbEx5mkYMDCig7ggLBDa8.QX1YTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Redirecting standard output (stdout) of a command to a file using the `>` operator.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Appending output
>In this challenge, we learn about appending to a file rather than overwriting it, using the `>>` operator. We are tasked with redirecting the output of `/challenge/run` twice to the same file to capture both parts of the flag.

## Solve:
- First ran `/challenge/run > the-flag`, which overwrote the file with only the first part of the output.
- Then ran `/challenge/run >> the-flag` to append the second part of the output, successfully capturing the complete flag in `the-flag`.

```
hacker@piping~appending-output:~$ /challenge/run > the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ /challenge/run >> the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat the-flag
 |
\|/ This is the first half:
 v
pwn.college{AqTywhAG545Dqy3mvjsit2DawDI.QX3ATO0wCN2AzNwIzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

## Flag
```
pwn.college{AqTywhAG545Dqy3mvjsit2DawDI.QX3ATO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `>>` operator to append standard output to an existing file without overwriting its previous contents.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Redirecting errors
>In this challenge, we learn about redirecting standard error (stderr) separately from standard output (stdout). We are tasked with redirecting stdout to `myflag` and stderr to `instructions`.

## Solve:
- Executed `/challenge/run > myflag 2> instructions` to redirect stdout (file descriptor 1) to `myflag` and stderr (file descriptor 2) to `instructions`.
- The challenge verified both redirections independently and provided the flag.

```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{sgmmTaepM9Op7NcTNgHFhhi8QIA.QX3YTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{sgmmTaepM9Op7NcTNgHFhhi8QIA.QX3YTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `2>` to redirect standard error (stderr) to a specific file, independent of standard output (stdout).

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Redirecting input
>In this challenge, we learn about redirecting standard input (stdin) from a file using the `<` operator. We are tasked with creating a file containing specific text and redirecting it into the challenge program.

## Solve:
- Created a file named `PWN` containing the text `COLLEGE` using `echo COLLEGE > PWN`.
- Executed `/challenge/run < PWN` to redirect the file's contents as standard input to the program, which read the value and output the flag.

```
hacker@piping~redirecting-input:~$ ls
COLLEGE  a  instructions  myflag  not-the-flag  the-flag
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{Af1QblfZ1K3Ik1awH6uBs81k2Gp.QXwcTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{Af1QblfZ1K3Ik1awH6uBs81k2Gp.QXwcTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `<` operator to redirect the contents of a file into the standard input (stdin) of a command.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Grepping stored results
>In this challenge, we learn about combining output redirection with the `grep` command to filter stored results. We are tasked with redirecting the output of `/challenge/run` to a file and then searching that file for the flag.

## Solve:
- Redirected the output of `/challenge/run` to `/tmp/data.txt` using `>`.
- Used `cat /tmp/data.txt | grep pwn` to filter the stored output and reveal the flag.

```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ cat /tmp/data.txt | grep pwn
pwning
pwn.college{UXfINt0As522O1x1fKMgkB0N5zM.QX4EDO0wCN2AzNwIzW}
pwned
pwns
pwn
```

## Flag
```
pwn.college{UXfINt0As522O1x1fKMgkB0N5zM.QX4EDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Redirecting command output to a file and using `grep` to search for specific patterns within that stored file.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Grepping live output
>In this challenge, we learn about piping the live standard output of a command directly into `grep`. We are tasked with running `/challenge/run` and piping its output to `grep pwn` to filter the results in real-time.

## Solve:
- Executed `/challenge/run | grep pwn`, which piped the live stdout of the challenge program directly into `grep`.
- This filtered the output in real-time, revealing the flag.

```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/sacz532zgiacvg7mva9v6gbfmyw427i3-gnugrep-3.12/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwned
pwn
pwns
pwn.college{gIutTQFSxUXmAZPQlVj8v1_6SE6.QX5EDO0wCN2AzNwIzW}
pwning
```

## Flag
```
pwn.college{gIutTQFSxUXmAZPQlVj8v1_6SE6.QX5EDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the pipe `|` operator to pass the live standard output of one command directly as standard input to another command (`grep`).

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Grepping errors
>In this challenge, we learn about redirecting standard error (stderr) to standard output (stdout) so it can be piped into `grep`. We are tasked with filtering the error output of `/challenge/run`.

## Solve:
- Executed `/challenge/run 2>&1 | grep pwn` to redirect stderr (file descriptor 2) to stdout (file descriptor 1).
- Piped the combined output into `grep pwn` to find the flag hidden within the error messages.

```
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep pwn
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/sacz532zgiacvg7mva9v6gbfmyw427i3-gnugrep-3.12/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwns
pwning
pwn
pwn.college{I7ywAB4kNbZL8caeKNYFCHMA6Sv.QX1ATO0wCN2AzNwIzW}
pwned
```

## Flag
```
pwn.college{I7ywAB4kNbZL8caeKNYFCHMA6Sv.QX1ATO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `2>&1` to redirect standard error to standard output, allowing it to be processed by a pipe `|`.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Filter withing grep -v
>In this challenge, we learn about using `grep -v` to invert the match and filter out unwanted lines. We are tasked with running `/challenge/run` and filtering out lines containing "DECOY" to reveal the flag.

## Solve:
- Executed `/challenge/run | grep -v "DECOY"`, which piped the output of the challenge program into `grep` with the `-v` flag.
- This successfully filtered out the decoy lines, leaving only the flag.

```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v "DECOY"
pwn.college{EYfTHSoYJ0WxWDxro9PK4D235Hx.0FOxEzNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{EYfTHSoYJ0WxWDxro9PK4D235Hx.0FOxEzNxwCN2AzNwIzW}
```

## Concepts Learnt
- Using the `-v` flag with `grep` to invert the match and display only lines that do *not* contain the specified pattern.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Duplicating piped data with tee
>In this challenge, we learn about using the `tee` command to duplicate piped data, allowing us to both save it to a file and pass it along the pipeline. We are tasked with inspecting the output of `/challenge/pwn` to find a secret code.

## Solve:
- First ran `/challenge/pwn | tee test | /challenge/college` to save the output to `test` while passing it to `college`.
- After inspecting `test` with `cat` to find the required secret argument (`ciMXiXOs`), reran the pipeline with the correct argument: `/challenge/pwn --secret ciMXiXOs | /challenge/college` to get the flag.

```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee test | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to save the first
attempt to a file, inspect the saved output, and then retry the pipeline with
what you learned.
hacker@piping~duplicating-piped-data-with-tee:~$ cat test
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "ciMXiXOs"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret ciMXiXOs | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{ciMXiXOsnfhm-Q-ZkBurn_JYDPV.QXxITO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{ciMXiXOsnfhm-Q-ZkBurn_JYDPV.QXxITO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `tee` to duplicate standard input, writing it to a file while also passing it to standard output for further piping.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Process substituion for input
>In this challenge, we learn about using process substitution `<()` to treat the output of a command as a file. We are tasked with comparing the output of two challenge programs using `diff`.

## Solve:
- Executed `diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)` to compare the live output of the two commands as if they were files.
- This revealed the added line containing the flag.

```
hacker@piping~process-substitution-for-input:~$ diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
45a46
> pwn.college{QGWMyTcvxWjtdzV5VxiBxWeHrSc.0lNwMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{QGWMyTcvxWjtdzV5VxiBxWeHrSc.0lNwMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using process substitution `<()` to pass the output of a command as a file argument to another command (like `diff`).

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Writing to multiple programs
>In this challenge, we learn about using process substitution `>()` with `tee` to write output to multiple programs simultaneously. We are tasked with sending the same rapidly changing data to both `/challenge/the` and `/challenge/planet`.

## Solve:
- Executed `/challenge/hack | tee >(/challenge/the) >(/challenge/planet)` to duplicate the output of `/challenge/hack`.
- This fed the data directly into the standard input of both challenge programs simultaneously, receiving the flag.

```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
1582125922246019216
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{YQaBmQeAVgSUckVOlt8gsfWaYAn.QXwgDN1wCN2AzNwIzW}
```

## Flag
```
pwn.college{YQaBmQeAVgSUckVOlt8gsfWaYAn.QXwgDN1wCN2AzNwIzW}
```

## Concepts Learnt
- Combining `tee` with process substitution `>()` to write standard output to the input of multiple commands concurrently.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Split-piping stderr and stdout
>In this challenge, we learn about redirecting standard error and standard output to different process substitutions simultaneously. We are tasked with sending stderr to `/challenge/the` and stdout to `/challenge/planet`.

## Solve:
- Executed `/challenge/hack 2> >(/challenge/the) > >(/challenge/planet)`.
- This redirected stderr (via `2>`) to the first process substitution and stdout (via `>`) to the second process substitution, successfully satisfying the redirection requirements.

```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{UqmFK_AxVE-7PaMVxr336kYE86z.QXxQDM2wCN2AzNwIzW}
```

## Flag
```
pwn.college{UqmFK_AxVE-7PaMVxr336kYE86z.QXxQDM2wCN2AzNwIzW}
```

## Concepts Learnt
- Combining stderr redirection (`2>`) and stdout redirection (`>`) with process substitution `>()` to split output streams to different programs.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)

---

# Named pipes
>In this challenge, we learn about creating and using named pipes (FIFOs) with `mkfifo`. We are tasked with redirecting the output of `/challenge/run` into a named pipe and reading from it to retrieve the flag.

## Solve:
- Created a named pipe at `/tmp/flag_fifo` using `mkfifo`.
- Redirected the output of `/challenge/run` into the pipe (`> /tmp/flag_fifo`) and simultaneously read from it using `cat /tmp/flag_fifo`, which unblocked the pipe and revealed the flag.

```
hacker@piping~named-pipes:~$ mkfifo myfifo
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{U1eHxe-KEGs6idPygVR34_e3tR6.01MzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{U1eHxe-KEGs6idPygVR34_e3tR6.01MzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using `mkfifo` to create named pipes (FIFOs).
- Understanding how FIFOs block execution until both a reader and a writer are connected.

## References
- [pwn.college](https://pwn.college/linux-luminarium/piping/)
