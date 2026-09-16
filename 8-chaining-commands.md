# Chaining with Semicolons
>In this challenge, we learn how to chain multiple commands together using the `;` operator. This operator separates commands sequentially, executing them one after another regardless of whether the preceding command succeeds or fails.

## Solve:
- Chained the `/challenge/pwn` and `/challenge/college` commands using a semicolon (`;`) to execute them in sequence.

```bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{IOlAnxQ33wy40u6GoRcuxaerhkA.QX1UDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{IOlAnxQ33wy40u6GoRcuxaerhkA.QX1UDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Command chaining in the shell.
- Using the `;` operator for unconditional sequential execution.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Building on Success
>In this challenge, we learn how to chain commands conditionally using the `&&` (AND) operator. This operator ensures that the second command is executed *only* if the first command succeeds.

## Solve:
- Chained the `/challenge/first-success` and `/challenge/second` commands using the `&&` operator.
- Since the first command succeeded, the second command executed, satisfying the challenge and outputting the flag.

```bash
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{QXN3KmiooE-MvGyqbeY3Nmf56C-.0lM0MDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{QXN3KmiooE-MvGyqbeY3Nmf56C-.0lM0MDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using the `&&` (AND) operator to execute commands only upon prior success.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Handling Failure
>In this challenge, we learn how to chain commands using the `||` (OR) operator. This operator ensures that the second command is executed *only* if the first command fails (i.e., exits with a non-zero status code), providing error handling.

## Solve:
- Chained the `/challenge/first-failure` and `/challenge/second` commands using the `||` operator.
- Because the first command failed, the shell executed the second command, satisfying the challenge and outputting the flag.

```bash
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{kOfDmOKkoXe94svhg293DCrsRsc.01M0MDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{kOfDmOKkoXe94svhg293DCrsRsc.01M0MDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using the `||` (OR) operator to execute a fallback command upon failure.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Your First Shell Script
>In this challenge, we learn how to automate command execution by writing a shell script. We are tasked with placing multiple commands into a file and executing that file using `bash`.

## Solve:
- Created a file named `x.sh` and wrote the `/challenge/pwn` and `/challenge/college` commands into it.
- Made the script executable using `chmod +x` and executed it using `bash x.sh` to retrieve the flag.

```bash
hacker@chaining~your-first-shell-script:~$ echo /challenge/pwn > x.sh
hacker@chaining~your-first-shell-script:~$ echo /challenge/college >> x.sh
hacker@chaining~your-first-shell-script:~$ chmod +x x.sh
hacker@chaining~your-first-shell-script:~$ ./x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{M81cQqpw_9wrTZPXtSdPjP4wJ31.QXxcDO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{M81cQqpw_9wrTZPXtSdPjP4wJ31.QXxcDO0wCN2AzNwIzW}
```

## Concepts Learnt
- Creating and executing shell scripts using `bash`.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Redirecting Script Output
>In this challenge, we learn how to redirect the standard output of an entire shell script into another command. We are tasked with piping the combined output of our script into a verification program.

## Solve:
- Executed the previously created `x.sh` script and used the pipe operator (`|`) to send its standard output directly as standard input to `/challenge/solve`.
- The verification program processed the piped output and returned the flag.

```bash
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{UN12SpQ0D9TH-f2GohcmNUNx7o_.QX4ETO0wCN2AzNwIzW}
```

## Flag
```
pwn.college{UN12SpQ0D9TH-f2GohcmNUNx7o_.QX4ETO0wCN2AzNwIzW}
```

## Concepts Learnt
- Using the `|` operator with script execution.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Executable Shell Scripts
>In this challenge, we learn how to make a shell script directly executable. This allows the script to be run as a standalone command without explicitly invoking the `bash` interpreter.

## Solve:
- Created a script named `x.sh` containing the `/challenge/solve` command.
- Used `chmod +x` to grant execute permissions to the file.
- Executed the script directly using `./x.sh` to retrieve the flag.

```bash
hacker@chaining~executable-shell-scripts:~$ echo "/challenge/solve" > x.sh && chmod +x x.sh && ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{YmMrUmx26q9xklZzaFJok3fv0N_.QX0cjM1wCN2AzNwIzW}
```

## Flag
```
pwn.college{YmMrUmx26q9xklZzaFJok3fv0N_.QX0cjM1wCN2AzNwIzW}
```

## Concepts Learnt
- Modifying file permissions with `chmod +x`.
- Direct execution of shell scripts.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Understanding Shebangs
>In this challenge, we learn about the shebang (`#!`) directive. This special character sequence at the beginning of a script tells the operating system which interpreter to use when the script is executed directly.

## Solve:
- Created `/home/hacker/solve.sh` with a proper shebang (e.g., `#!/bin/bash`) as the first line.
- Configured the script to output "hack the planet", made it executable, and ran `/challenge/run` to verify the setup and receive the flag.

```bash
hacker@chaining~understanding-shebangs:~$ vim solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{kPYt-76uGcIbdEI2rIHVa9s_cOf.0VOzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{kPYt-76uGcIbdEI2rIHVa9s_cOf.0VOzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- How the OS uses shebangs to determine the script interpreter.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Scripting with Arguments
>In this challenge, we learn how to access and manipulate command-line arguments passed to a shell script using positional parameters.

## Solve:
- Created `/home/hacker/solve.sh` to accept two arguments and print them in reverse order (e.g., using `echo "$2 $1"`).
- Made the script executable and ran `/challenge/run` to verify the logic and obtain the flag.

```bash
hacker@chaining~scripting-with-arguments:~$ vim solve.sh
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{Akj_neZW_GFwSZV7r-5NCzNklXT.0VNzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{Akj_neZW_GFwSZV7r-5NCzNklXT.0VNzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Accessing command-line arguments in Bash using positional parameters (`$1`, `$2`, etc.).

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Scripting with Conditionals
>In this challenge, we learn how to implement basic conditional logic in a shell script using `if` statements to control the flow of execution based on input.

## Solve:
- Created `/home/hacker/solve.sh` that takes a single argument and uses an `if` statement to output "college" only if the argument is exactly "pwn".
- Made the script executable and ran `/challenge/run` to verify the conditional logic and receive the flag.

```bash
hacker@chaining~scripting-with-conditionals:~$ vim solve.sh
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{IWWWL_wgvbQjyK2lM8ELbirOCZJ.0lNzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{IWWWL_wgvbQjyK2lM8ELbirOCZJ.0lNzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using `if` statements for conditional execution in Bash.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Scripting with Default Cases
>In this challenge, we learn how to handle fallback conditions in shell scripts by combining `if` and `else` statements to cover all possible input scenarios.

## Solve:
- Created `/home/hacker/solve.sh` that outputs "college" if the argument is "pwn", and "nope" for any other input using an `if/else` block.
- Made the script executable and ran `/challenge/run` to verify the complete conditional logic.

```bash
hacker@chaining~scripting-with-default-cases:~$ vim solve.sh
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{IdZ_rfhXdcvn-0lpj9tZChwfZOC.01NzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{IdZ_rfhXdcvn-0lpj9tZChwfZOC.01NzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using `if/else` control flow in shell scripts.
- Implementing default fallback cases for unmatched conditions.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Scripting with Multiple Conditions
>In this challenge, we learn how to evaluate multiple distinct conditions in a shell script using `if`, `elif`, and `else` statements to create complex branching logic.

## Solve:
- Created `/home/hacker/solve.sh` that maps specific inputs to outputs: "hack" -> "the planet", "pwn" -> "college", "learn" -> "linux", and a default "unknown" for anything else.
- Made the script executable and ran `/challenge/run` to verify the multi-branch conditional logic.

```bash
hacker@chaining~scripting-with-multiple-conditions:~$ vim solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ sudo chmod +x solve.sh
sudo: workspace is not privileged
hacker@chaining~scripting-with-multiple-conditions:~$ chmod +x solve.sh
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{YtmBDMNGy62uDdpvgYqER065HNA.0FOzMDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{YtmBDMNGy62uDdpvgYqER065HNA.0FOzMDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Using `elif` statements for multiple conditional branches.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)

---

# Reading Shell Scripts
>In this challenge, we learn how to analyse existing shell scripts for hardcoded secrets.

## Solve:
- Used the `cat` command to read the source code of `/challenge/run`.
- Identified the hardcoded password ("hack the PLANET") within the `if` statement.
- Executed `/challenge/run` and provided the extracted password when prompted to retrieve the flag.

```bash
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/usr/bin/exec-suid -- /bin/bash -p

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{YhZ8yrJo2FCueCCgGApdmiOVqJB.0lMwgDOxwCN2AzNwIzW}
```

## Flag
```
pwn.college{YhZ8yrJo2FCueCCgGApdmiOVqJB.0lMwgDOxwCN2AzNwIzW}
```

## Concepts Learnt
- Analyzing shell script source code.

## References
- [pwn.college](https://pwn.college/linux-luminarium/chaining/)
