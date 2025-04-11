# Linux-File-Directory-Permissions
A simple guide to Linux file &amp; directory permissions. Learn about read, write, execute modes, symbolic &amp; numeric notation (like rwx / chmod 755), ownership (chown), groups, and special bits (setuid, setgid, sticky). Perfect for beginners and quick reference.

🧱 Permission Basics
Each file/directory has three types of access:

r → Read (view file content or list directory)

w → Write (edit file or add/delete inside directory)

x → Execute (run script or enter directory)

And these apply to three types of users:

Owner – The user who owns the file

Group – Users in the same group as the file

Others – Everyone else

🧾 Viewing Permissions

To check file permissions:

ls -l

Example output:

-rwxr-xr--  1 john devs  4096 Apr 10  file.sh

Breakdown:

- → regular file (d would be directory)

rwx → owner permissions (read, write, execute)

r-x → group permissions (read, execute)

r-- → others permissions (read only)

🔧 Changing Permissions

✅ chmod – Change Permissions

Symbolic Mode:

chmod u+x file.sh      # Add execute to user

chmod g-w file.txt     # Remove write from group

chmod o=r file.txt     # Set others to read only

Numeric (Octal) Mode:

Each permission has a value:

r = 4

w = 2

x = 1

Then sum them up:

User Type	rwx	Binary	Value

User	rwx	111	7

Group	r-x	101	5

Others	r--	100	4

Example:

chmod 754 file.sh

# 7 = rwx (user)

# 5 = r-x (group)

# 4 = r-- (others)

🔁 Changing Ownership

✅ chown – Change File Owner

sudo chown newuser file.txt

✅ chgrp – Change Group

sudo chgrp newgroup file.txt

✅ Both user and group:

sudo chown user:group file.txt

📁 Directory Permissions

Permission	Effect

r	List files in the directory

w	Create, delete, or rename files

x	Enter the directory (cd)
So, a directory needs execute (x) permission to access its contents, even if you can read them.

🔐 Common Permission Examples
Goal	Command

Make a script executable	chmod +x script.sh

Full access for owner only	chmod 700 file.txt

Read-only for everyone	chmod 444 file.txt

Make dir accessible to all	chmod 755 mydir/

📌 Pro Tips

Avoid 777 unless absolutely necessary. It gives everyone full access, which is insecure.

Use groups for better permission management across teams.

Use umask to set default permission behavior for new files.

🔍 Check Permissions with:

ls -ld filename        # Check file or directory permissions

stat filename          # Detailed info including permissions
