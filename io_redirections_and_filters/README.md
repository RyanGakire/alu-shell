README - Shell, I/O Redirections and Filters
===========================================

This file documents the small shell scripts created for the "Shell, I/O Redirections and Filters" project.
Each script is a two-line executable (first line: shebang `#!/bin/bash`; second line: the single command).
Make each script executable before running:
  chmod +x <script_name>

Notes
-----
- Most scripts read from standard input unless they explicitly reference a file (e.g., /etc/passwd).
- Examples show typical usage; adapt input redirection or pipes as needed.
- Ensure your environment has the utilities used (grep, cut, tr, find, sort, uniq, awk, rev, paste, head, etc.).

Scripts index (0 through 26)
---------------------------

0.  0-hello_world
    Purpose: prints “Hello, World”, followed by a new line to the standard output.

1.  1-confused_smiley
    Purpose: displays a confused smiley "(Ôo)'.

2.  2-hellofile
    Purpose: Displays the content of the /etc/passwd file.

3.  3-twofiles
    Purpose: Displays the content of /etc/passwd and /etc/hosts

4.  4-lastlines
    Purpose: Displays the last 10 lines of /etc/passwd

5.  5-firstlines
    Purpose: Displays the first 10 lines of /etc/passwd

6.  6-third_line
    Purpose: Displays the third line of the file iacta.

7.  7-file
    Purpose: creates a file named exactly \*\\'"Best School"\'\\*$\?\*\*\*\*\*:) containing the text Best School ending by a new line.

8.  8-cwd_state
    Purpose: writes into the file ls_cwd_content the result of the command ls -la. If the file ls_cwd_content already exists, it should be overwritten. If the file ls_cwd_content does not exist, create it.

9.  9-duplicate_last_line
    Purpose: duplicates the last line of the file iacta

10. 10-no_more_js
    Purpose: deletes all the regular files (not the directories) with a .js extension that are present in the current directory and all its subfolders.

11. 11-directories
    Purpose: counts the number of directories and sub-directories in the current directory.

- The current and parent directories should not be taken into account
- Hidden directories should be counted

12. 12-newest_files
    Purpose: displays the 10 newest files in the current directory.

13. 13-unique
    Purpose: takes a list of words as input and prints only words that appear exactly once.

14. 14-findthatword
    Purpose: Display lines containing the pattern “root” from the file /etc/passwd

15. 15-countthatword
    Purpose: Display the number of lines that contain the pattern “bin” in the file /etc/passwd

16. 16-whatsnext
    Command:
      #!/bin/bash
      grep -A 3 "root" /etc/passwd
    Purpose:
      Print every line that contains "root" and the three lines that follow each match.
    Usage:
      chmod +x 16-whatsnext
      ./16-whatsnext

17. 17-hidethisword
    Command:
      #!/bin/bash
      grep -v "bin" /etc/passwd
    Purpose:
      Print lines from /etc/passwd that do NOT contain the substring "bin".
    Usage:
      chmod +x 17-hidethisword
      ./17-hidethisword

18. 18-letteronly
    Command:
      #!/bin/bash
      grep -E '^[A-Za-z]' /etc/ssh/sshd_config
    Purpose:
      Print only lines that start with a letter from /etc/ssh/sshd_config.
    Usage:
      chmod +x 18-letteronly
      ./18-letteronly

19. 19-A_to_Z
    Command:
      #!/bin/bash
      tr 'Ac' 'ze'
    Purpose:
      Read from stdin and replace uppercase A with z and lowercase c with e.
    Usage:
      chmod +x 19-A_to_Z
      echo "A cat and a car" | ./19-A_to_Z

20. 20-hiago
    Command:
      #!/bin/bash
      tr -d 'cC'
    Purpose:
      Delete all occurrences of lowercase c and uppercase C from stdin.
    Usage:
      chmod +x 20-hiago
      echo "Chicago" | ./20-hiago

21. 21-reverse
    Command:
      #!/bin/bash
      rev
    Purpose:
      Reverse each input line (reads from stdin).
    Usage:
      chmod +x 21-reverse
      echo "Reverse" | ./21-reverse

22. 22-users_and_homes
    Command:
      #!/bin/bash
      cut -d: -f1,6 /etc/passwd | sort -t: -k1,1 | tr ':' ' '
    Purpose:
      Display username and home directory from /etc/passwd, sorted by username.
    Usage:
      chmod +x 22-users_and_homes
      ./22-users_and_homes

23. 23-empty
    Command:
      #!/bin/bash
      find . -empty -printf "%f\n"
    Purpose:
      Find empty files and empty directories under the current directory (includes hidden),
      printing only the basename, one per line. Output ends with a newline.
    Usage:
      chmod +x 23-empty
      ./23-empty

24. 24-gifs
    Command:
      #!/bin/bash
      find . -type f -iname '*.gif' -printf '%f\n' | rev | cut -d. -f2- | rev | sort -f
    Purpose:
      List .gif filenames (case-insensitive), print names without the final .gif extension,
      and sort case-insensitively.
    Usage:
      chmod +x 24-gifs
      ./24-gifs

25. 25-acrostic
    Command:
      #!/bin/bash
      cut -c1 | paste -sd '' -
    Purpose:
      Build an acrostic by taking the first character of each input line and concatenating them
      into a single string followed by a newline.
    Usage:
      chmod +x 25-acrostic
      cat poem.txt | ./25-acrostic

26. 26-top_talkers
    Command:
      #!/bin/bash
      cut -f1 | sort | uniq -c | sort -nr | head -11 | awk '{print $2}'
    Purpose:
      From TSV web server logs read on stdin, display the top 11 hosts/IPs (first column)
      by number of requests, most active first.
    Usage:
      chmod +x 26-top_talkers
      cat web_log.tsv | ./26-top_talkers


