# The PATH Variable
>In this challenge, we learn about the `PATH` environment variable and how the shell uses it to locate executable files. We are tasked with preventing the challenge script from deleting the flag by manipulating the `PATH`.

## Solve:
- Examined the current `PATH` using `echo $PATH` and located specific commands using `which`.
- Cleared the `PATH` variable by setting `PATH=""`, which prevents the shell from finding the `rm` command.
- Executed `/challenge/run`, which failed to remove the `/flag` file due to the missing `rm` command, thus outputting the flag.

```bash
hacker@path~the-path-variable:~$ echo $PATH
/run/challenge/bin:/run/dojo/bin:/challenge/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~the-path-variable:~$ which rm
/run/dojo/bin/rm
hacker@path~the-path-variable:~$ which cd
which: no cd in (/run/challenge/bin:/run/dojo/bin:/challenge/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin)
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ ls
bash: ls: command not found
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{A3JRnEe9iWAEUUf2IrSmKtnQDZo.QX2cDM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{A3JRnEe9iWAEUUf2IrSmKtnQDZo.QX2cDM1wCN2AzNwIzW}
```

## Concepts Learnt
- How to view and clear the `PATH` variable to control or restrict command execution.

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)

---

# Setting PATH
>In this challenge, we learn how to set the `PATH` environment variable to a specific directory, allowing the shell to find a required command that is not in the default system paths.

## Solve:
- Set the `PATH` environment variable to `/challenge/more_commands` using `PATH="/challenge/more_commands"`.
- Executed `/challenge/run`, which successfully found and invoked the `win` command from the newly set path, outputting the flag.

```bash
hacker@path~setting-path:~$ PATH="/challenge/more_commands"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{4ITBZ_Djd79LAOzD3xnV8OsVjpZ.QX1cjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{4ITBZ_Djd79LAOzD3xnV8OsVjpZ.QX1cjM1wCN2AzNwIzW}
```

## Concepts Learnt
- How to assign a new value to the `PATH` environment variable.

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)

---

# Finding Commands
>In this challenge, we learn how to use the `which` command to locate the executable path of a command, and then use that directory information to find related files.

## Solve:
- Used `which win` to discover the directory where the `win` executable is located (`/challenge/paths/32450/`).
- Listed the contents of that directory to find the flag file.
- Used the `cat` command with the absolute path to read the `flag` file and retrieve the flag.

```bash
hacker@path~finding-commands:~$ which win
/challenge/paths/32450/win
hacker@path~finding-commands:~$ cat /challenge/paths/32450/
flag  win
hacker@path~finding-commands:~$ cat /challenge/paths/32450/flag
pwn.college{sHxGRg0TdHDuDkxSpVq1fXYyEUZ.01NzEzNxwCN2AzNwIzW}
```

## Flag
```
pwn.college{sHxGRg0TdHDuDkxSpVq1fXYyEUZ.01NzEzNxwCN2AzNwIzW}
```

## Concepts Learnt
- Using the `which` command to find the absolute path of an executable.

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)

---

# Adding commands
>In this challenge, we learn how to add a custom directory to the existing `PATH` environment variable so the shell can find and execute our own scripts alongside system commands.

## Solve:
- Created a custom executable script named `win` in the home directory that outputs the flag (`echo "cat /flag" > win` followed by `chmod +x win`).
- Appended the home directory to the existing `PATH` using `PATH="$PATH:/home/hacker"`.
- Executed `/challenge/run`, which successfully found and ran our custom `win` script, revealing the flag.

```bash
hacker@path~adding-commands:~$ echo "cat /flag" > win
hacker@path~adding-commands:~$ ls
COLLEGE  instructions  not-the-flag  the-flag
PWN      myfifo        solve.sh      win
a        myflag        test          x.sh
hacker@path~adding-commands:~$ chmod +x win
hacker@path~adding-commands:~$ PATH="$PATH:/home/hacker"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{g5v332G4L2L97DkeMz_VbL9E8P6.QX2cjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{g5v332G4L2L97DkeMz_VbL9E8P6.QX2cjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Appending a directory to the `PATH` variable using `PATH="$PATH:/new/directory"`.

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)

---

# Hijacking Commands
>In this challenge, we learn how to hijack command execution by placing a custom script with the same name as a system command in a directory that appears earlier in the `PATH`.

## Solve:
- Created a custom script named `rm` in the home directory (using `vim`) containing a command to read the flag (e.g., `/run/dojo/bin/cat /flag`).
- Overwrote the `PATH` to only include the home directory using `PATH="/home/hacker"`, giving it the highest priority.
- Executed `/challenge/run`, which attempted to call `rm`. Due to the modified `PATH`, it executed our hijacked `rm` script instead of the system binary, successfully printing the flag.

```bash
hacker@path~hijacking-commands:~$ vim rm
hacker@path~hijacking-commands:~$ PATH="/home/hacker"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{IgCK9Sv-eHjxMCd5HC4nVU3qHJy.QX3cjM1wCN2AzNwIzW}
hacker@path~hijacking-commands:~$ /run/dojo/bin/cat rm
/run/dojo/bin/cat /flag
```

## Flag
```
pwn.college{IgCK9Sv-eHjxMCd5HC4nVU3qHJy.QX3cjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Command hijacking via `PATH` manipulation.

## References
- [pwn.college](https://pwn.college/linux-luminarium/path/)
