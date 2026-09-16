# Intro to Commands
>In this challenge, we learn about the basics of entering commands through the shell. We are shown an example of the user inputting `whoami` into the terminal and getting their username back. We are taught to invoke commands by their case-sensitive name.

## Solve:
- Used the case-sensitive command "hello" and got the output

```
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{4JcwrUC-kSSkCsiOAv8GmZAdK77.QX3YjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{4JcwrUC-kSSkCsiOAv8GmZAdK77.QX3YjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Running commands in the terminal
- Making sure the case of the command is correct
- `whoami` gives the name of the user running the command

## References
- [pwn.college](https://pwn.college/linux-luminarium/hello/)

# Intro to Arguments
>In this challenge, we learn about passing arguments to the commands we learnt about in the previous exercise.

## Solve:
- Passed the argument `hackers` to `hello` to get my desired output

```
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{sKaperXv29qlI-_noA8E3UOspel.QX4YjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{sKaperXv29qlI-_noA8E3UOspel.QX4YjM1wCN2AzNwIzW}
```

## Concepts Learnt
- To give shorthand arguments (Ex. -n or -h), we use a single hyphen while long form arguments (Ex. --help and --output) require the usage of double hyphens.
- Operands can be passed without any hyphen

## References
- [pwn.college](https://pwn.college/linux-luminarium/hello/)

# Command History
> In this challenge, we learn about scrolling back through the **history** and finding commands we used previously.

## Solve:
- Inputted `history` into the terminal and got back my previous commands
```
hacker@hello~command-history:~$ history
    1  hello
    2  exit
    3  exit
    4  ls
    5  ls -a
    6  pwn
    7  hello
    8  whoami
    9  .exit
   10  hello heackers
   11  hello hackers
   12  history
   13  history
   14  the flag is pwn.college{EAiUTkK9tXaCnccuXsx5TnjeDac.0lNzEzNxwCN2AzNwIzW}
   15  history
   16  history
   17  exit
   18  hello
   19  hello hackers
   20  the flag is pwn.college{EAiUTkK9tXaCnccuXsx5TnjeDac.0lNzEzNxwCN2AzNwIzW}
   21  history
```

## Flag
```
pwn.college{EAiUTkK9tXaCnccuXsx5TnjeDac.0lNzEzNxwCN2AzNwIzW}
```

## Concepts Learnt
- The `history` command is useful for scrolling back to find the previous commands

## References
- [pwn.college](https://pwn.college/linux-luminarium/hello/)
