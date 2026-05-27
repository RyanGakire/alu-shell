Shell Permissions Project

This project contains a series of Bash scripts that demonstrate user, group, owner, and permission operations on files and directories.
Each script is exactly two lines long: a shebang (#!/bin/bash) on line 1 and a single command on line 2.

---

Scripts Overview

1. 0-iam_betty
Switches the current user to the user 'betty'. 
Command: su betty

2. 1-who_am_i
Prints the effective username of the current user.
Command: whoami

3. 2-groups
Prints all the groups the current user is part of.
Command: groups

4. 3-new_owner
Changes the owner of `hello` file to the user 'betty'.
Command: chown betty hello

5. 4-empty
Creates an empty file named hello.
Command: touch hello

6. 5-execute
Adds execute permission to the file hello for the owner.
Command: chmod u+x hello

7. 6-multiple_permissions
Adds execute permission to hello for owner and group, and read permission for others.
Command: chmod ug+x,o+r hello

8. 7-everybody
Adds execute permission to hello for all users (owner, group, others).
Command: chmod a+x hello

9. 8-James_Bond
Sets permissions so that only others have full access (rwx), while owner and group have none.
Command: chmod 007 hello

10. 9-John_Doe
Sets permissions of hello to -rwxr-x-wx (owner: rwx, group: r-x, others: -wx).
Command: chmod 753 hello

11. 10-mirror_permissions
Sets the permissions of hello to match those of olleh.
Command: chmod --reference=olleh hello

12. 11-directories_permissions
Adds execute permission to all subdirectories of the current directory for all users.
Command: chmod a+x */

13. 12-directory_permissions
Creates a directory named my_dir with full permissions for everyone.
Command: mkdir -m 777 my_dir

14. 13-change_group
Changes the group ownership of hello to a specified group (e.g., school).
Command: chgrp school hello

15. 14-change_owner_and_group
Changes the owner of hello to vincent and the group to staff.
Command: chown vincent:staff hello

16. 15-symbolic_link_permissions
Changes the owner and group of the symbolic link _hello itself to vincent and staff.
Command: chown -h vincent:staff _hello

17. 16-if_only
Changes the owner of hello to vincent only if it is currently owned by guillaume.
Command: chown --from=guillaume vincent hello

---

Notes
- All scripts must be exactly two lines long: the shebang (#!/bin/bash) and one command.
- Replace any placeholder commands above (marked with <insert ...>) with the exact command you used in each script.
- Make each script executable with: chmod +x <script_name>
- Test each script and verify results with commands like ls -l hello or ls -ld my_dir.

If you want, I can now:
- Fill in the exact commands for tasks 0–3 and 13 if you paste the commands you used, or
- Generate a final README.md with the exact commands substituted where you confirm them.

