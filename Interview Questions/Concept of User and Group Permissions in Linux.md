In Linux, **user and group permissions** control who can access files and directories and what actions they can perform on them. This ensures security and proper access control.

## 1. **Users and Groups**

- **User**: A person or system that has an account on the Linux system. Each user has a unique **User ID (UID)**.
- **Group**: A collection of users who share permissions. Each group has a unique **Group ID (GID)**.

## 2. **Permission Types**

Each file or directory in Linux has three types of permissions:

- **Read (r)**: Allows viewing the file content or listing directory contents.
- **Write (w)**: Allows modifying the file or creating/deleting files in a directory.
- **Execute (x)**: Allows running a file as a program/script or entering a directory.

## 3. **Permission Levels**

Permissions are assigned at three levels:

- **Owner (User - u)**: The person who created the file.
- **Group (g)**: Users who belong to the group assigned to the file.
- **Others (o)**: Everyone else.

## 4. **Viewing Permissions**

Use the `ls -l` command to see permissions:

```
-rwxr--r-- 1 user group 1234 Mar 10 12:34 file.txt
```

Breakdown:

- `-` → File type (`-` for file, `d` for directory)
- `rwx` → Owner has **read, write, execute**
- `r--` → Group has **read only**
- `r--` → Others have **read only**

## 5. **Changing Permissions**

- **chmod** (change mode): Modify file permissions
    - Example: `chmod 755 file.txt`
- **chown** (change owner): Change file owner
    - Example: `chown user1 file.txt`
- **chgrp** (change group): Change file group
    - Example: `chgrp group1 file.txt`

### Example:

To allow only the owner to read and write but deny access to others:

```
chmod 600 file.txt
```

This sets permissions as `rw-------` (only the owner can read/write).

This system ensures security by restricting access to only authorized users. 🚀