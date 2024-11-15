# Linux Permissions, Groups, and Environment Variables

## Principle of Least Privilege

In Linux, users are given the minimum permissions necessary to perform their tasks.

- **Root Restrictions**: In root directories, normal users cannot create directories or files. This permission is reserved for superuser (root).
- **Home Directory**: Users have full control within their home directory.
  - **rm -rf /** inside root does not work without `sudo`.
  - Inside the user's home directory, `rm -rf` works without `sudo`.

## Root and Sudo Commands

- **sudo mkdir [folder_name]**: Creates a directory with root privileges.
- **sudo whoami**: Displays the current user, showing "root" when using `sudo`.
- **sudo su**: Switches to the root user.
- **sudo useradd [username]**: Adds a new user.
- **sudo passwd [username]**: Sets a password for the specified user.

## Group Management

- **Groups**: Linux uses groups to manage permissions.
- **sudo usermod -aG [group] [username]**: Adds a user to a specified group.
  - Example: `sudo usermod -aG sudo brian` adds Brian to the `sudo` group, granting him sudo privileges.

---

# File and Directory Permissions

### File Types and Permissions

- **Normal Files**: Indicated by a dash (`-`) at the beginning, like `-rw-r--r--`.
- **Directory**: Indicated by a "d" (`d`) at the beginning, like `drwxr-xr-x`.

### Permissions Explained

- **r**: Read permission.
- **w**: Write permission.
- **x**: Execute permission.
- Example: `drwxrwxr-x` indicates a directory with read, write, and execute permissions for the owner and group, and read and execute permissions for others.

### Changing Ownership and Permissions

- **sudo chown [user]:[group] [file]**: Changes ownership of a file.
  - Example: `sudo chown ubuntu:ubuntu /hello.txt` changes ownership of `hello.txt` to the user `ubuntu`.
- **chmod**: Used to modify file or directory permissions.
  - **Numeric Mode**: Each permission set can be represented as a number:
    - 7 = rwx
    - 6 = rw
    - 5 = r-x
  - Example: `sudo chmod 777 [file_or_directory]` grants read, write, and execute permissions to everyone.

### Permission Examples

- **700**: Only the owner has full access.
- **644**: The owner can read/write, while the group and others can only read.
- **664**: The owner and group can read/write, others can only read.

---

## Environment Variables

Environment variables are used to store information for the shell session.

- **printenv**: Lists all environment variables.
- **echo $[VARIABLE_NAME]**: Displays the value of an environment variable.
  - Example: `echo $USER` shows the current username.

### Setting Environment Variables

- **Temporary Variables**: Can be set for a single session.
  - Example: `GREETING="Hello"`; `echo $GREETING` outputs "Hello".
- **Permanent Variables**: Set in files like `/etc/environment` for system-wide availability.

### Adding Variables to `.bashrc`

- **vim ~/.bashrc**: Opens the `.bashrc` file for editing.
- **export [VAR_NAME]="[value]"**: Adds a new environment variable.
  - Example: `export NEW_VAR="Good Things"`.

### Applying Changes

- **source ~/.bashrc**: Reloads `.bashrc` to apply new environment variables to the current session.

