# Linux File Operations and Commands

## Viewing File Content

- **tail textfile.txt**: Outputs the last 10 lines of `textfile.txt`.
- **head textfile.txt**: Outputs the first 10 lines of `textfile.txt`.
  - **-n**: Specifies the number of lines to show.
    - Example: `tail -n 3 textfile.txt` displays the last 3 lines.
- **tail -f textfile.txt**: Follows `textfile.txt` in real-time, showing lines as they are added, useful for monitoring logs.

### Appending to Files

- **echo "text" >> textfile.txt**: Appends `"text"` to the end of `textfile.txt`.

---

## Directory Management

- **mkdir -p folder1/folder2/folder3**: Creates nested folders (e.g., `folder1`, `folder2` inside `folder1`, and `folder3` inside `folder2`).

### Moving and Deleting Files

- **mv**: Moves files or renames them.
  - Example: `mv demo.txt new-name.txt` renames `demo.txt` to `new-name.txt`.
- **rm [foldername]**: Removes a directory.
- **rm -r**: Recursively deletes a folder and its contents.
- **rm -rf /**: Force-deletes everything on the Linux system (be extremely cautious; this can destroy the entire system).

> **Warning**: The `rm` command permanently deletes files. To avoid accidental deletion, consider using `trash-cli` to send files to the trash instead of permanently deleting them.

### Trash Commands

- **trash-put text.txt**: Moves `text.txt` to the trash.
- **trash-restore**: Restores a file from the trash.
- **trash-list**: Lists files in the trash.

---

## Copying Files and Directories

- **cp [source_file] [destination_file]**: Copies a file to a new location.
- **cp [file] [foldername]**: Copies a file to a specific folder.
- **cp -r foldername_source foldername_dest**: Copies a folder and its contents recursively to another location.

---

## File Compression and Archiving

- **tar -cf archive.tar file1.txt folder1**: Creates an uncompressed archive containing `file1.txt` and `folder1`.
- **tar -czf archive.tar.gz file1.txt folder1**: Creates a compressed archive (gzip).
- **tar -xzf archive.tar.gz -C [destination_folder]**: Extracts the archive to the specified folder.

---

# Wildcards and File Patterns

Wildcards can be used to match multiple files or patterns.

- **touch file{1,2,3,4}.txt**: Creates files `file1.txt`, `file2.txt`, `file3.txt`, and `file4.txt`.
- **touch file-{a,b,c}.txt**: Creates `file-a.txt`, `file-b.txt`, and `file-c.txt`.
- **ls file-*:** Lists all files that start with `file-`.

### Range Expansion

- **touch file{1..10}.txt**: Creates `file1.txt` through `file10.txt`.
- **touch {a..z}.txt**: Creates files `a.txt` to `z.txt`.

---

# Output Streams and Redirection

- Output from one program can be redirected to the input of another using streams and pipes.
- **echo "This is the text" > new-file.txt**: Writes `"This is the text"` to `new-file.txt`.
- **cat new-file.txt >> file2.txt**: Appends the contents of `new-file.txt` to `file2.txt`.
  
> **Tip**: Use `>` to overwrite a file and `>>` to append to a file.
