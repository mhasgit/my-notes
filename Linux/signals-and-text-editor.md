# Linux Signals and Text Editors

## Signals

Signals are notifications sent to a program to indicate an event or interrupt its execution.

- **tail -f .bash_history**: Shows the contents of `.bash_history` as they are added in real-time, allowing you to see commands being executed on the go.

### Common Signals

- **Ctrl + C**: Sends the SIGINT signal to interrupt a running program.
- **Ctrl + D**: Sends the SIGQUIT signal, often used to log out of a shell or terminate a program.
- **SIGTERM**: A signal terminator, used by the OS to kill a program gracefully.

### Killing Processes

- **kill -l**: Lists all available signals that can be sent to processes.
- **kill -9 [Process ID]**: Sends a SIGKILL signal to terminate a specific process immediately.

---

## Text Editors

Linux offers a variety of text editors for editing files from the command line.

### Nano

- **nano [filename]**: Opens a file in the `nano` text editor, which is a simple and user-friendly editor.

### Vim

- **vim [filename]**: Opens a file in the `vim` text editor, which is more powerful and has multiple modes.
- **vi**: An alternative to Vim, often pre-installed on Unix-based systems.

---

# Vim Modes and Commands

Vim has different modes, including **insert mode** (for editing text) and **command mode** (for executing commands).

### Essential Vim Commands

- **:q**: Quits Vim.
  - **:q!**: Forces Vim to quit without saving unsaved changes.
- **:100d**: Deletes 100 lines from above the current line.
- **Escape**: Switches back to command mode from insert mode.
- **i**: Enters interactive/insert mode.
- **:w**: Saves changes to the file.
- **:wq**: Saves changes and quits Vim.
- **:help tutor**: Opens Vim's built-in tutorial.

> **Tip**: If you’re stuck in Vim, use `:q!` to quit without saving changes. This will exit Vim immediately.

### Other Editors

- **Emacs**: Another powerful text editor, known for extensive customization options.

---

# Reading Files

Linux provides several commands for reading and managing file content.

- **less**: A program for viewing file contents one screen at a time. This is useful for reading large files.
  - Example: `less [filename]` (e.g., `less textfile.txt`)
  - **/search_term**: Use `/` to search for a word within the file while using `less`.
- **more**: Similar to `less`, but older and less feature-rich. `more` lacks backward scrolling.
- **man**: Displays the manual for a specific command.
  - Example: `man less` or `less --help` provides the manual or summary for `less`.

> **Tip**: Every program has a manual. Use `man [command]` to get help on a command.

- **cat**: Concatenates and displays the contents of files.
  - Example: `cat [filename]` prints the entire file content.

---

# Additional Tips

- **Ctrl + C**: Copy command.
- **Ctrl + V**: Paste command.
- **Ctrl + Z**: Suspend a job temporarily.
