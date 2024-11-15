# SSH and SFTP (Secure File Transfer Protocol)

## Setting Up SSH Key-Based Authentication

1. **Generate SSH Key Pair**:
   - Command:
     ```bash
     ssh-keygen -t rsa
     ```
   - This creates a public and private RSA key pair (e.g., `id_rsa` and `id_rsa.pub`).

2. **Navigate to the `.ssh` Directory**:
   - Command:
     ```bash
     cd ~/.ssh
     ls
     ```
   - You should see two files: `id_rsa` (private key) and `id_rsa.pub` (public key).

3. **On the Second Machine**:
   - Create an `.ssh` directory if it doesn’t exist:
     ```bash
     mkdir ~/.ssh
     cd ~/.ssh
     ```
   - Create or edit the `authorized_keys` file to store authorized public keys:
     ```bash
     vi authorized_keys
     ```

4. **Copy the Public Key**:
   - On the first machine, copy the contents of `id_rsa.pub`:
     ```bash
     cat ~/.ssh/id_rsa.pub
     ```
   - Paste this content into the `authorized_keys` file on the second machine.

5. **Set Permissions**:
   - On the second machine, set appropriate permissions:
     ```bash
     chmod 700 ~/.ssh
     chmod 600 ~/.ssh/authorized_keys
     ```
   - This ensures only the user has read/write/execute permissions on `.ssh` and `authorized_keys`.

6. **Connecting via SSH**:
   - Find the IP address of the second machine using `ipconfig` (Windows) or `ifconfig` (Linux).
   - Connect to the second machine from the first:
     ```bash
     ssh [username]@[IP]
     ```
   - This establishes a secure connection if the setup is successful.

---

## SFTP (Secure FTP)

SFTP is a secure way to transfer files over SSH.

- **Connecting with SFTP**:
  - Command:
    ```bash
    sftp [username]@[IP]
    ```
  - Once connected, use common commands like `pwd`, `ls`, and `cd` to navigate directories.

- **File Transfer Commands**:
  - **Upload a File**:
    ```bash
    put [local_file]
    ```
    - Transfers a file from the local system to the remote system.
  - **Download a File**:
    ```bash
    get [remote_file]
    ```
    - Downloads a file from the remote system to the local system.

> **Tip**: While in SFTP, you can use `!` to run local shell commands.

---

# Wget and Curl

## Wget

Wget is used for downloading files from the web and supports recursive downloads.

- **Downloading Files**:
  - Command:
    ```bash
    wget [URL]
    ```
    - Downloads a file from the specified URL.

- **Running Scripts with Wget**:
  - Download a shell script and execute it:
    ```bash
    wget [script_url]
    chmod +x script.sh
    ./script.sh
    ```
  - Ensure the script is executable before running it.

- **Recursive Downloading**:
  - Wget can download entire websites:
    ```bash
    wget -r [URL]
    ```
  - Useful for downloading all files in a folder structure from a website.

> **Note**: Wget is particularly useful for straightforward file downloads.

## Curl

Curl is a versatile tool for transferring data from or to a server, allowing for more control over requests.

- **Basic Usage**:
  - Command:
    ```bash
    curl [URL]
    ```
    - Fetches the content from the specified URL.

- **API Testing**:
  - Useful for interacting with APIs to test endpoints:
    ```bash
    curl -X GET [API_ENDPOINT]
    ```
  - Can send requests like GET, POST, PUT, DELETE, and more.

> **Tip**: Curl is often used in API development to test endpoints. It’s also more flexible than Wget as it can pipe data into other commands, making it ideal for advanced tasks.

