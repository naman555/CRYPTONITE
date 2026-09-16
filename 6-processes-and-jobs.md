# Listing Processes
>In this challenge, we learn about viewing the currently running processes on the system. We are tasked with finding a hidden challenge executable that is already running in the background and executing it to retrieve the flag.

## Solve:
- Used the `ps aux` command to list all running processes on the system.
- Identified the hidden challenge executable (`/challenge/13328-run-3999`) from the process list.
- Executed the identified binary to get the flag.

```
hacker@processes~listing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   752 ?        Ss   17:36   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo
root           7  0.0  0.0   7136  2716 ?        S    17:36   0:00 /run/dojo/bin/sleep 6h
root         110  0.0  0.0 232596  4008 ?        S    17:36   0:00 /challenge/13328-run-3999
root         113  0.0  0.0 235016  3496 ?        S    17:36   0:00 sleep 6h
hacker       124  0.0  0.0  37980 22864 ?        Sl   17:36   0:00 /nix/store/nzhm2kbnlpp13kwvk192825y8pykhiag-ttyd-1.7.7/bin/ttyd --
hacker       126  0.0  0.0 232860  4964 pts/0    Ss   17:36   0:00 /run/dojo/bin/bash --login
hacker       131  0.0  0.0 235228  4400 pts/0    R+   17:38   0:00 ps aux
hacker@processes~listing-processes:~$ /challenge/13328-run-3999
Yahaha, you found me! Here is your flag:
pwn.college{8WxkEWMH68QduWh3kzZuxabHaSf.QX4MDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{8WxkEWMH68QduWh3kzZuxabHaSf.QX4MDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `ps aux` command to list all currently running processes.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Killing Processes
>In this challenge, we learn about terminating running processes using the `kill` command. We are tasked with finding and killing a specific blocking process so that the main challenge executable can run successfully.

## Solve:
- Used `ps aux` to list processes and find the PID of the blocking `/challenge/dont_run` process (PID 110).
- Used the `kill 110` command to terminate the process.
- Executed `/challenge/run` to get the flag.

```
hacker@processes~killing-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   748 ?        Ss   17:40   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo
root           7  0.0  0.0   7136  2800 ?        S    17:40   0:00 /run/dojo/bin/sleep 6h
root         109  0.0  0.0   4332  2892 ?        S    17:40   0:00 su -c /challenge/.launcher hacker
hacker       110  0.0  0.0 232596  4068 ?        Ss   17:40   0:00 /challenge/dont_run
hacker       111  0.0  0.0 235016  3392 ?        S    17:40   0:00 sleep 6h
hacker       122  0.1  0.0  37980 22804 ?        Sl   17:40   0:00 /nix/store/nzhm2kbnlpp13kwvk192825y8pykhiag-ttyd-1.7.7/bin/ttyd --
hacker       124  0.0  0.0 232960  4940 pts/0    Ss   17:40   0:00 /run/dojo/bin/bash --login
hacker       130  0.0  0.0 235228  4396 pts/0    R+   17:41   0:00 ps aux
hacker@processes~killing-processes:~$ kill 110
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{IVG7hg0MeRNZgVKbT0Zm8X81KHB.QXyQDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{IVG7hg0MeRNZgVKbT0Zm8X81KHB.QXyQDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `kill` command to terminate a process by its Process ID (PID).
- Using `ps` to find the PID of a specific running process.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Interrupting Processes
>In this challenge, we learn about sending interrupt signals to foreground processes. We are tasked with stopping a running challenge program using Ctrl+C to trigger the flag output.

## Solve:
- Executed `/challenge/run`, which prompted to be interrupted.
- Pressed `Ctrl-C` to send a SIGINT signal and interrupt the process, which then output the flag.

```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{QAZ6TgdUk5jv2-cQjguvnqAra5E.QXzQDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{QAZ6TgdUk5jv2-cQjguvnqAra5E.QXzQDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `Ctrl-C` to send a SIGINT signal and interrupt/terminate a foreground process.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Killing Misbehaving Processes
>In this challenge, we practice identifying and terminating background processes that are interfering with our terminal. We are tasked with killing a spamming Python script so the real flag can be written to a FIFO.

## Solve:
- Used `ps aux` to find the PID of the misbehaving Python decoy process (PID 114).
- Used `kill 114` to terminate the spamming process.
- Executed `/challenge/run` and read the genuine flag from `/tmp/flag_fifo`.

```
hacker@processes~killing-misbehaving-processes:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.0   1056   752 ?        Ss   17:47   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/d
root           7  0.0  0.0   7136  2804 ?        S    17:47   0:00 /run/dojo/bin/sleep 6h
root         111  0.0  0.0   2696  1656 ?        S    17:47   0:00 sleep 6h
root         112  0.0  0.0   2696  1600 ?        S    17:47   0:00 sleep 6h
root         113  0.0  0.0   4332  2932 ?        S    17:47   0:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
hacker       114  0.0  0.0  16440 12272 ?        Ss   17:47   0:00 /usr/bin/python3 /challenge/decoy
hacker       125  0.0  0.0  37980 22812 ?        Sl   17:47   0:00 /nix/store/nzhm2kbnlpp13kwvk192825y8pykhiag-ttyd-1.7.7/bin/ttyd --port 7681 --
hacker       127  0.0  0.0 232976  4984 pts/0    Ss   17:47   0:00 /run/dojo/bin/bash --login
hacker       132  0.0  0.0 235228  4428 pts/0    R+   17:52   0:00 ps aux
hacker@processes~killing-misbehaving-processes:~$ kill 114
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
pwn.college{n8yBHysjxmyND8PNR1OYnMm.jg1hEvKG.cojcX8dvL7gaom}
pwn.college{mK-k-YTlIwqCjC8a2urtN7HmY9DTPeX-Zg.Unjhl3HVWSyt}
pwn.college{-6iVj2TMKTHBjemkm5-nTSC8wNrVbTsKS8ylO0cHmNKEAqP}
pwn.college{Qr27tgwrVb2bMbaYP.Jj.EXnTplprOlPYexbhpxu46NqIiH}
pwn.college{Q5tLbpBgHtGJ9BCswWNwYxCQ6zTxXcoenaNTwRdEVSohcch}
pwn.college{Lms9wTc.jtxvsfy0cdtbgrOGkjjRkCYgHkUpNUtsFXX2nVc}
pwn.college{J0Dgc7gK-JKOMyFZrwRQMTOAOBxZ2eaW7KIA9rZnYCbcQng}
pwn.college{LoRn8QYjQQkMVBo5pIImUtAV9oydgGwy2fvKJq8hu7ba8Cm}
pwn.college{57U28vl6Uwjas7i-QN1V9dOoEiBH.-WS3hArxTUmGn346S0}
pwn.college{EQ1waFLcU0otJvARKiZnpi3T-Mj4yUXTiYzYW21wpCXQKnq}
pwn.college{l8He8cSIMHmiJj5JxARhlxXoK4Z4BeZ0IndRR07rE4awwr8}
pwn.college{pkQ2e6xDBymc7ib-zGRZ8rpaD55tvMD0tMyO36lBvSNepXJ}
pwn.college{gTrUhFC-PBBzvgGt50xWsNLrYhq6TDUhFBarQF4U13dN4jc}
pwn.college{9TY5d350eN3LPGMYbFzT8ccajTH.pbgJVb8y2ZQVmSNmv.i}
pwn.college{x0vTXPIp-mIKBvCmaU6gHrSzG1NjE2PFHq5Fx1x5-yxNLWN}
pwn.college{mRHOMENifU.1oDJTdMKb.1B-jjuRr4g52erhSQGX8qQyqMT}
pwn.college{T6XXBGwYQdfx98ZGi5Fd9x-FFLawrwge4XC6ZBOR5hj29ea}
pwn.college{3xwAxDZ3zhkMPOEUSOdZuRthVlqH2UMMp1bG4kAzoqAojfd}
pwn.college{k4nUfErmwDAPOIYyPlDwMIfk2AXPRsm.FPiPvJOPm0EaH6e}
pwn.college{0.GP0nZrBvgmSh1rkbCJxM0Hc2W6GcWS1-pss4R4HOm14xU}
pwn.college{ILu8CTBoPqz.uz5HlQ373DVDJrVB2J35P1K4E6BwoR3LILH}
pwn.college{ulMm8i-werEJuqws77yyJ1hD1U8hXFvnouCXPh9whpWkROd}
pwn.college{5yV3uhRxmErTEH8BJxfZHMP6KWlHcO0FVpiV91UeK5piWr3}
pwn.college{S1c7SPs2HhEmH3MhzoYs4vSwcr3smPEPGkkcRkNAns3VxBD}
pwn.college{EygfjSWkbL75VElih6hjg1EhsfC4DLQOqxI8uAnPSjcG2vK}
pwn.college{UdPVruIGIDl04sTFPLFYvZTNlYjmBTePbdXc3kA1F.NNA-z}
pwn.college{k4YXvSYJX1YhsjkvtLPDoHzqHF0.0FNzMDOxwCN2AzNwIzW}^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{k4YXvSYJX1YhsjkvtLPDoHzqHF0.0FNzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{k4YXvSYJX1YhsjkvtLPDoHzqHF0.0FNzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Identifying and killing background or misbehaving processes using their PID.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Suspending Processes
>In this challenge, we learn about suspending foreground processes using Ctrl+Z. We are tasked with pausing a running instance of the challenge program and launching a second instance to satisfy the verification check.

## Solve:
- Executed `/challenge/run` and pressed `Ctrl-Z` to send a SIGTSTP signal, suspending the process.
- Ran `/challenge/run` a second time while the first instance was suspended, satisfying the challenge condition and receiving the flag.

```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         120     115  0 18:04 pts/0    00:00:00 /bin/bash -p /challenge/run
root         122     120  0 18:04 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                    /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         120     115  0 18:04 pts/0    00:00:00 /bin/bash -p /challenge/run
root         127     115  0 18:04 pts/0    00:00:00 /bin/bash -p /challenge/run
root         129     127  0 18:04 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{s9fbolspfAjhXiVQWuvL34wHLsc.QX1QDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{s9fbolspfAjhXiVQWuvL34wHLsc.QX1QDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `Ctrl-Z` to send a SIGTSTP signal and suspend a foreground process.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Resuming Processes
>In this challenge, we learn about resuming suspended processes back into the foreground. We are tasked with suspending the challenge program and then bringing it back to resume its execution.

## Solve:
- Executed `/challenge/run` and pressed `Ctrl-Z` to suspend it.
- Used the `fg` command to resume the suspended process in the foreground, which then output the flag.

```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                    /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{sfUmtckYsuMFL1_XdFHmhhje05c.QX2QDO0wCN2AzNwIzW}
Don't forget to press Enter to quit me!

Goodbye!
```

## Flag
```
pwn.college{sfUmtckYsuMFL1_XdFHmhhje05c.QX2QDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `fg` command to resume a suspended process in the foreground.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Background Processes
>In this challenge, we learn about moving suspended processes into the background. We are tasked with suspending the challenge program, backgrounding it, and then running a second instance.

## Solve:
- Executed `/challenge/run` and pressed `Ctrl-Z` to suspend it.
- Used the `bg` command to resume the process in the background.
- Ran `/challenge/run` again, which detected the backgrounded instance and output the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         120 S+   /bin/bash -p /challenge/run
root         122 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                    /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         120 S    /bin/bash -p /challenge/run
root         130 S    sleep 6h
root         131 S+   /bin/bash -p /challenge/run
root         133 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{MheWBUH8nteI2rk7i7U8xVkfzPX.QX3QDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{MheWBUH8nteI2rk7i7U8xVkfzPX.QX3QDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `bg` command to resume a suspended process in the background.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Foreground Processes
>In this challenge, we learn about bringing background processes back to the foreground. We are tasked with suspending a process, moving it to the background, and then foregrounding it again.

## Solve:
- Executed `/challenge/run`, suspended it with `Ctrl-Z`, and backgrounded it with `bg`.
- Used the `fg` command to bring the background process back to the foreground, satisfying the challenge and receiving the flag.

```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                    /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{MiRyBgPBwpKsaNuIz7mzKTnPWp1.QX4QDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{MiRyBgPBwpKsaNuIz7mzKTnPWp1.QX4QDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using `fg` to bring a backgrounded or suspended process back to the foreground.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Starting Background Processes
>In this challenge, we learn about launching commands directly into the background. We are tasked with starting the challenge executable in the background immediately upon execution.

## Solve:
- Appended `&` to the command (`/challenge/run &`) to start the process directly in the background.
- The process detected it was backgrounded upon startup and output the flag.

```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 123
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{kSShD8_K8rAahFMy_wMovv5ZXAa.QX5QDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{kSShD8_K8rAahFMy_wMovv5ZXAa.QX5QDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `&` operator at the end of a command to start it directly in the background.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)

---

# Process Exit Codes
>In this challenge, we learn about checking the exit status of the most recently executed command. We are tasked with capturing an error code generated by a program and submitting it to another program.

## Solve:
- Executed `/challenge/get-code` which exited with an error.
- Used `echo $?` to print the exit code of the last executed command (180).
- Passed this code to `/challenge/submit-code 180` to get the flag.

```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
180
hacker@processes~process-exit-codes:~$ /challenge/submit-code 180
CORRECT! Here is your flag:
pwn.college{EUyzUXEYNt2zxao6YbDXWhelLFU.QX5YDO1wCN2AzNwIzW}
```

## Flag
```
pwn.college{EUyzUXEYNt2zxao6YbDXWhelLFU.QX5YDO1wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `$?` environment variable to retrieve the exit status/code of the most recently executed foreground pipeline.

## References
- [pwn.college](https://pwn.college/linux-luminarium/processes/)
