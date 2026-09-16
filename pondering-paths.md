# The Root
>In this challenge, we learn about the basics of the Linux filesystem and absolute paths. The filesystem starts at the root directory `/`, and we are tasked with invoking a program located directly in this root directory to retrieve the flag.

## Solve:
- Executed the challenge program using its absolute path `/pwn` to get the desired output.

```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{MUasLNyfab_KUx_-rIaIYVTJWbo.QX4cTO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{MUasLNyfab_KUx_-rIaIYVTJWbo.QX4cTO0wCN2AzNwIzW}
```

## Concepts Learnt
- The Linux filesystem is a tree structure that starts at the root directory (`/`).
- An absolute path starts with `/` and specifies the exact location of a file or directory from the root.
- Programs can be invoked by providing their absolute path on the command line.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# Program and absolute paths
>In this challenge, we learn about navigating slightly more complicated paths. Challenges in pwn.college are typically located in the `/challenge` directory, which resides directly in the root directory (`/`). We must execute the `run` program using its full absolute path.

## Solve:
- Invoked the challenge program using its absolute path `/challenge/run` to get the desired output.

```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{ctVIUAO7IeEUkvvqud7xFjb0yfc.QX1QTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{ctVIUAO7IeEUkvvqud7xFjb0yfc.QX1QTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Constructing absolute paths by traversing from the root directory (`/`).
- Executing binaries by specifying their exact location in the filesystem.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# Position thy self
>In this challenge, we learn about navigating the Linux filesystem using the `cd` (change directory) command. The challenge requires us to execute the `/challenge/run` program from a specific directory, teaching us how the current working directory affects execution.

## Solve:
- Attempted to run `/challenge/run` from the home directory, which resulted in an error indicating the wrong directory.
- Used the `cd /` command to change the current working directory to the root directory.
- Re-executed `/challenge/run` from the correct directory to receive the flag.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /
hacker@paths~position-thy-self:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QoUs0FKAyD8JU8FzhpbWE3SpNdW.QX2QTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{QoUs0FKAyD8JU8FzhpbWE3SpNdW.QX2QTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `cd` command to navigate the filesystem.
- Understood the concept of the Current Working Directory (CWD).
- Recognising how the shell prompt reflects the current directory (e.g., `~` for home, `/` for root).

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# Position elsewhere
>In this challenge, we practice directory navigation multiple times. We are required to execute the `/challenge/run` program from five different specific directories sequentially, as prompted by the challenge program.

## Solve:
- Followed the program's prompts to change directories using the `cd` command.
- Navigated to `/sys`, `/usr/include`, `/etc/apt/sources.list.d`, `/etc`, and finally `/usr/share/build-essential`.
- Executed `/challenge/run` after each successful directory change until the final flag was awarded.

```
hacker@paths~position-elsewhere:~$ /challenge/run
Starting level 1.
Incorrect...
You are not currently in the /sys directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /sys/
hacker@paths~position-elsewhere:/sys$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Moving on to level 2
Please use the `cd` utility to change directory to /usr/include
hacker@paths~position-elsewhere:/sys$ cd /usr/include/
hacker@paths~position-elsewhere:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Moving on to level 3
Please use the `cd` utility to change directory to /etc/apt/sources.list.d
hacker@paths~position-elsewhere:/usr/include$ cd /etc/apt/sources.list.d/
hacker@paths~position-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Moving on to level 4
Please use the `cd` utility to change directory to /etc
hacker@paths~position-elsewhere:/etc/apt/sources.list.d$ cd /etc/
hacker@paths~position-elsewhere:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Moving on to level 5
Please use the `cd` utility to change directory to /usr/share/build-essential
hacker@paths~position-elsewhere:/etc$ cd /usr/share/bu
bug/             build-essential/
hacker@paths~position-elsewhere:/etc$ cd /usr/share/build-essential/
hacker@paths~position-elsewhere:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{43hcLPGpVjXceN97qitJGdhTXgd.QX3QTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{43hcLPGpVjXceN97qitJGdhTXgd.QX3QTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Repeatedly changing the current working directory to meet specific program requirements.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# Implicit relative paths, from /
>In this challenge, we learn about relative paths, which do not start with `/` and are interpreted relative to the current working directory. We must change our current directory to `/` and invoke the challenge program using a relative path.

## Solve:
- Changed the current working directory to the root directory using `cd /`.
- Invoked the challenge program using the relative path `challenge/run`, which resolves to `/challenge/run` from the root directory.

```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{oLA6m6mGbecjvK-2rXfl-nUVCog.QX5QTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{oLA6m6mGbecjvK-2rXfl-nUVCog.QX5QTN0wCN2AzNwIzW}
```

## Concepts Learnt
- The distinction between absolute and relative paths.
- Executing programs using implicit relative paths without a leading `./`.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# Explicit relative paths, from /
>In this challenge, we explore explicit relative paths using the `.` (current directory) and `..` (parent directory) special entries. We must ensure our current working directory is `/` and use a relative path beginning with `.` to invoke the challenge.

## Solve:
- Ensured the current working directory was `/` using `cd /`.
- Executed the challenge program using the explicit relative path `./challenge/run`.

```
hacker@paths~explicit-relative-paths-from-:/$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{007bVz1aWAP92_Rx8NNhhTsCNkn.QXwUTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{007bVz1aWAP92_Rx8NNhhTsCNkn.QXwUTN0wCN2AzNwIzW}
```

## Concepts Learnt
- The purpose and usage of the `.` (current directory) and `..` (parent directory) special directory entries.
- Constructing explicit relative paths to clearly denote execution from the current directory.
- How `./` differentiates a local executable from a system-wide command.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# implicit relative path
>In this challenge, we learn that Linux avoids automatically searching the current directory for executables when a "naked" command is provided, as a security measure. We must explicitly tell the shell to execute a program in the current directory.

## Solve:
- Navigated to the challenge directory using `cd /challenge/`.
- Executed the program using the explicit relative path `./run` to instruct the shell to run the executable in the current directory, avoiding the "command not found" error.

```
hacker@paths~implicit-relative-path:~$ cd /challenge/
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gqH4uI1M8KYKec1tI8lV9ycBSCz.QXxUTN0wCN2AzNwIzW}
```

## Flag
```
pwn.college{gqH4uI1M8KYKec1tI8lV9ycBSCz.QXxUTN0wCN2AzNwIzW}
```

## Concepts Learnt
- Linux security design
- The necessity of using `./` to explicitly execute binaries located in the current working directory.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)

---

# home sweet home
>In this challenge, we learn about the user home directory and the `~` shorthand. We are tasked with passing an argument to `/challenge/run` that is an absolute path inside the home directory, but the argument itself must be three characters or less before shell expansion.

## Solve:
- Recognized that `~` expands to `/home/hacker` and is exactly one character.
- Executed `/challenge/run ~/a`, providing a path that is 3 characters (`~/a`) before expansion, which resolves to the absolute path `/home/hacker/a` and successfully retrieves the flag.

```
hacker@paths~home-sweet-home:~$ /challenge/run ~/a
Writing the file to /home/hacker/a!
... and reading it back to you:
pwn.college{sIFlKJKjlGogQZg1CuA7Zpwv5DB.QXzMDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{sIFlKJKjlGogQZg1CuA7Zpwv5DB.QXzMDO0wCN2AzNwIzW}
```

## Concepts Learnt
- The concept of the user home directory and its default location in Linux.
- Shell tilde (`~`) expansion and how it simplifies path specification.

## References
- [pwn.college](https://pwn.college/linux-luminarium/paths/)
