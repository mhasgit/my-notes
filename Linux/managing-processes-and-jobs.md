# Managing Processes and Background Jobs in Linux

## Environment Variables and Bash Files

- **Environment Variables in `.bashrc`**: Environment variables can be stored in `.bashrc` for each shell session.
- **Global Environment Variables**: Placed in `/etc/bashrc`, these apply to all users.

## Process Management

- **ps**: Shows all running processes.
- **sleep 10 &**: Runs the `sleep 10` command in the background.
- **kill -SIGKILL [PID]**: Forcefully stops a process with the specified Process ID (PID).
- **ps aux**: Shows all running processes with detailed information.
- **ps aux | less**: Pipes process list output into `less` for easier viewing.
- **ps aux | grep "[process]"**: Filters for processes matching the specified term.

### Background and Foreground

- **sleep 1000**: Pauses the terminal for 1000 seconds.
- **Ctrl + Z**: Pauses the current foreground process.
- **jobs**: Lists background jobs.
- **bg [job_number]**: Resumes a paused job in the background.
- **fg [job_number]**: Brings a background job to the foreground.

## Screen and tmux

- **screen**: Allows multiple shell sessions within one terminal. Great for keeping programs running in the background even if the session is detached.
- **tmux**: Allows a split-screen view and advanced session handling.

---

# Exit Codes and Conditional Execution

- **Exit Codes**: Every program returns an exit code on completion.
  - **0**: Success.
  - **>0**: Failure.

- **echo $?**: Displays the exit code of the last command.

### Conditional Operators

- **||**: Executes the next command if the previous one fails.
  - Example: `false || echo "Failed"` prints "Failed" because `false` returned a non-zero exit code.
- **&&**: Executes the next command only if the previous one succeeds.
  - Example: `true && echo "Success"` prints "Success".

---

# Subcommands and SSH

## Subcommands

- **$(command)**: Executes a command within another command.
  - Example: `echo "Today is $(date)"` displays "Today is [current date]".
  - **Backticks**: An older syntax for subcommands: `` `command` ``.
  
## Understanding Bash Profiles

- **.bashrc**: Runs for every new terminal session.
- **.bash_profile**: Runs only for login shells. Use `.bashrc` for setting up environment variables to apply in each session.

### Different Shell Configurations

- **Zsh**: Uses `.zshrc`.
- **Fish Shell**: Uses `config.fish`.

> **Tip**: Stick to the relevant RC file for your shell (e.g., `.bashrc` for Bash).

---

# SSH (Secure Shell)

SSH allows you to remotely connect to and execute commands on another computer.

- **Setup SSH Access**:
  - **sudo useradd -m -g [group] [username]**: Creates a user for SSH access.
  - **sudo passwd [username]**: Sets a password for the user.
  - **su [username]**: Switches to the specified user.

> **Note**: SSH can be used to connect to remote servers on AWS, Azure, etc., allowing you to manage them as if you were physically present.
