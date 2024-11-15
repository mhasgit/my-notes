# Linux Commands and Tips

## Basic Commands

- **pwd**: Prints the present working directory.
- **ls**: Lists directory contents.
  - **-l**: Shows a long-form output.
  - **-a**: Includes hidden files and directories.
- **cd**: Changes the directory.
  - **cd ~**: Takes you to the home directory.
  - **cd ~/snap**: Takes you to the `snap` directory.
- **echo**: Outputs the provided text or variables to the screen.

## Flags

Flags allow you to turn a specific option on or off when using a command. Examples include:

- `pwd --help`: Shows help information for the `pwd` command.
- **ls -l**: Provides a long-form output of the directory listing.
- **ls -a**: Displays hidden files and directories.
- **-a**: Flag to include hidden files.
- **touch**: Creates a new empty file.
  - Example: `touch .hidden-file` creates a hidden file named `.hidden-file`.

### Combining Flags

- **(-)**: Shortened syntax to use a series of flags, such as `ls -la` or `ls -l -a`.
- **(--)**: Specifies a long-form flag. Example: `ls --ignore=snap` ignores the `snap` directory in the output.

- **ls -lsah**: Provides a complete overview with size, names, hidden files, etc.

> **Note**: The standard way is to put parameters immediately after the command, as in `ls -lsah snap`. Sometimes, the order matters.

## Multipass Commands

- **multipass launch --name instance --mem 2G --disk 10G**: Launches a new Multipass instance with specific memory and disk size.
- **multipass start [name]**: Starts the specified instance.
- **multipass stop [name]**: Stops the specified instance.
- **multipass delete [name]**: Deletes an instance (not recoverable).
- **multipass purge**: Permanently deletes all instances.
- **multipass shell [instance-name]**: Opens a shell in the specified instance.
- **multipass list**: Lists all active instances.

> **Note**: Use `net start multipass` or `net stop multipass` to start or stop the Multipass service.

---

# Navigating Directories and History

- **cd ~**: Takes you to the home directory.
- **cd ~/snap**: Navigates to the `snap` directory.

## Command History

- Any command entered in the terminal is stored in the Bash history, so be cautious on multi-user systems.
- **Double Tab**: Use double tab for auto-completing paths, like `cd home/`.

### Searching Bash History

- **Ctrl + R**: Opens reverse search in the terminal. Press `Ctrl + R` again to cycle through the results for the search term.
- **tail ~/.bash_history**: Views the recent commands from the Bash history file.

### Repeating the Last Command

- **!!**: Runs the last command again (e.g., `sudo !!` to rerun the last command with `sudo`).

---

# Common Shortcuts

- **clear** or **Ctrl + L**: Clears the terminal screen.
- **Copy**: `Ctrl + Shift + C`
- **Paste**: `Ctrl + Shift + V`
- **Beginning of Line**: `Ctrl + A`
- **End of Line**: `Ctrl + E`
- **Delete After Cursor**: `Ctrl + K` (this action is known as "yanking").
- **Yank (delete everything before cursor)**: `Ctrl + U`
- **Paste from Yank Buffer**: `Ctrl + Y`

> **Tip**: Knowing these shortcuts can help you work more efficiently in the terminal.

