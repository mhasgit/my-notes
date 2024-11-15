# Linux Commands for Process Management and Redirection

## Piping and Grep

Pipes are used to pass the output of one command as the input to another command.

- **cat ls.txt | grep "ls-error.txt"**: Connects `cat` with `grep` to search for "ls-error.txt" within the contents of `ls.txt`.
  
## Process Management

- **ps aux**: Lists all currently running processes.
- **ps aux | grep "ps aux"**: Finds instances of the `ps aux` command itself.
- **yes > /dev/null**: Runs `yes` in the background, sending output to `/dev/null` (a null device that discards all input).
- **ps aux | grep "yes"**: Searches for processes containing "yes" in their name.
- **kill -9 [PID]**: Forcefully kills the process with the specified Process ID (PID).

### Interactive Removal

- **rm -i [file]**: Prompts for confirmation before deleting `file`.
- **yes | rm -i [file]**: Automatically answers "yes" to all prompts, useful for batch deletions.

---

## User Identification

- **whoami**: Prints the username of the current user.
- **cat /etc/passwd**: Displays the contents of the `/etc/passwd` file, which contains user account information.

---

# Input and Output Redirection

## Standard Input, Output, and Error

- **ls -lsh > ls.txt**: Redirects the output of `ls -lsh` to `ls.txt`.
- **ls -lsh 2> ls-error.txt**: Redirects standard error to `ls-error.txt`.
- **cat non-existent-file.txt 2> error.txt**: Redirects the error message to `error.txt`.
- **ls -lsh > ls.txt 2>&1**: Redirects both output and error to the same file (`ls.txt`).
- **ls -lsh > /dev/null**: Redirects output to `/dev/null`, effectively ignoring it.

### Explanation of Streams

- **>**: Redirects standard output.
- **2>**: Redirects standard error.
- **>>**: Appends to a file instead of overwriting.
- **/dev/null**: Acts as a "black hole" to discard any input.

---

# Grep and Redirection Tips

- **cat file.txt | grep "search_term" > results.txt**: Searches for `"search_term"` in `file.txt` and writes the results to `results.txt`.
- **grep -r "search_term" .**: Recursively searches for `"search_term"` in the current directory and subdirectories.

> **Note**: `grep` does not show colored output by default in redirected files, but it can be visually parsed in terminals to differentiate matches.

---

## Useful Commands Summary

- **ps aux | grep "[process]"**: Filters out running processes containing `[process]`.
- **cat /etc/passwd**: View user details in the `passwd` file.
- **ls -lsh > ls-output.txt**: Redirects output to `ls-output.txt`.
- **yes | rm -i [file]**: Automates "yes" responses for interactive deletion.
