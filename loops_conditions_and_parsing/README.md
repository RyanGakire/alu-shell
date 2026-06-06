# Shell Scripting - Loops & Text Processing

A collection of Bash scripts demonstrating the use of loops, conditionals, and text processing tools.

---

## Scripts

### 1-for_best_school

Displays `Best School` 10 times using a `for` loop.

```bash
#!/usr/bin/env bash
# This script displays "Best School" 10 times using a for loop

for i in {1..10}; do
    echo "Best School"
done
```

**Usage:**
```
$ ./0-for_best_school
Best School
Best School
Best School
...
```

---

### 2-while_best_school

Displays `Best School` 10 times using a `while` loop.

```bash
#!/usr/bin/env bash
# This script displays "Best School" 10 times using a while loop

i=1
while [ $i -le 10 ]; do
    echo "Best School"
    i=$((i + 1))
done
```

**Usage:**
```
$ ./1-while_best_school
Best School
Best School
Best School
...
```

---

### 3-until_best_school

Displays `Best School` 10 times using an `until` loop.

```bash
#!/usr/bin/env bash
# This script displays "Best School" 10 times using an until loop

i=1
until [ $i -gt 10 ]; do
    echo "Best School"
    i=$((i + 1))
done
```

**Usage:**
```
$ ./2-until_best_school
Best School
Best School
Best School
...
```

---

### 4-if_9_say_hi

Displays `Best School` 10 times using a `while` loop, but on the 9th iteration also displays `Hi` on a new line.

```bash
#!/usr/bin/env bash
# This script displays "Best School" 10 times, but on the 9th iteration also displays "Hi"

i=1
while [ $i -le 10 ]; do
    echo "Best School"
    if [ $i -eq 9 ]; then
        echo "Hi"
    fi
    i=$((i + 1))
done
```

**Usage:**
```
$ ./3-if_9_say_hi
Best School
Best School
...
Best School
Hi
Best School
```

---

### 5-4_bad_luck_8_is_your_chance

Loops from 1 to 10 and displays different messages depending on the iteration using `if`, `elif`, and `else`.

- `bad luck` on the 4th iteration
- `good luck` on the 8th iteration
- `Best School` for all other iterations

```bash
#!/usr/bin/env bash
# This script loops from 1 to 10 and displays different messages for iterations 4, 8, and others

i=1
while [ $i -le 10 ]; do
    if [ $i -eq 4 ]; then
        echo "bad luck"
    elif [ $i -eq 8 ]; then
        echo "good luck"
    else
        echo "Best School"
    fi
    i=$((i + 1))
done
```

**Usage:**
```
$ ./4-if_elif_else
Best School
Best School
Best School
bad luck
Best School
Best School
Best School
good luck
Best School
Best School
```

---

### 6-superstitious_numbers

Displays numbers from 1 to 20 using a `while` loop and a `case` statement, with special messages for specific iterations.

- `bad luck from China` after the 4th number
- `bad luck from Japan` after the 9th number
- `bad luck from Italy` after the 17th number

```bash
#!/usr/bin/env bash
# This script displays numbers 1 to 20 with special messages for iterations 4, 9, and 17

i=1
while [ $i -le 20 ]; do
    echo $i
    case $i in
        4)
            echo "bad luck from China"
            ;;
        9)
            echo "bad luck from Japan"
            ;;
        17)
            echo "bad luck from Italy"
            ;;
    esac
    i=$((i + 1))
done
```

**Usage:**
```
$ ./5-4_bad_luck_8_is_your_chance
1
2
3
4
bad luck from China
...
9
bad luck from Japan
...
17
bad luck from Italy
18
19
20
```

---

### 7-clock

Displays the time for 12 hours and 59 minutes using nested `while` loops.

- Hours displayed from 0 to 12
- Minutes displayed from 1 to 59 under each hour

```bash
#!/usr/bin/env bash
# This script displays the time for 12 hours and 59 minutes

hour=0
while [ $hour -le 12 ]; do
    echo "Hour: $hour"
    minute=1
    while [ $minute -le 59 ]; do
        echo $minute
        minute=$((minute + 1))
    done
    hour=$((hour + 1))
done
```

**Usage:**
```
$ ./6-superstitious_numbers | head -n 10
Hour: 0
1
2
3
...
59
Hour: 1
1
...
```

---

## 8-for_ls

**Purpose:**
Displays the contents of the current directory in list format while showing only the part of each filename that appears after the first dash (`-`).

**Concepts used:**

* `for` loop
* Filename expansion (`*`)
* `cut` command

**Example:**

`100-read_and_cut` → `read_and_cut`

---

## 9-to_file_or_not_to_file

**Purpose:**
Checks the status of a file named `school` and displays information about it.

The script determines:

* Whether the file exists.
* Whether the file is empty or not.
* Whether the file is a regular file.

**Concepts used:**

* `if` / `else`
* File test operators:

  * `-e` (exists)
  * `-s` (not empty)
  * `-f` (regular file)

---

## 10-fizzbuzz

**Purpose:**
Displays numbers from 1 to 100.

Rules:

* Prints `FizzBuzz` for numbers divisible by both 3 and 5.
* Prints `Fizz` for numbers divisible by 3.
* Prints `Buzz` for numbers divisible by 5.
* Otherwise prints the number itself.

**Concepts used:**

* `for` loop
* Arithmetic expansion
* Conditional statements

---

## 12-tell_the_story_of_passwd

**Purpose:**
Reads the `/etc/passwd` file and displays selected information about each user.

Displayed fields:

* Username
* User ID (UID)
* Home directory

**Concepts used:**

* `while` loop
* `read`
* `IFS` (Internal Field Separator)

The script processes the file line by line and extracts only the required fields.

---

## 11-read_and_cut

**Purpose:**
Reads `/etc/passwd` and displays user information in a descriptive sentence.

Information included:

* Username
* Group ID
* Home directory
* Login shell
* Password field
* User ID

**Concepts used:**

* `while` loop
* `IFS`
* String formatting

---

### 13-lets_parse_apache_logs

Displays the visitor IP address along with the HTTP status code from an Apache log file using `awk`.

```bash
#!/usr/bin/env bash
# This script displays the visitor IP and HTTP status code from an Apache log file

awk '{print $1, $9}' apache-access.log
```

**Usage:**
```
$ ./7-clock | head -n 5
158.170.84.9 301
158.170.84.9 301
97.65.101.145 200
97.65.101.145 200
97.65.101.145 200
```

---

### 14-dig_the-data

Groups visitors by IP and HTTP status code, displaying the number of occurrences in descending order using `awk`, `sort`, and `uniq`.

```bash
#!/usr/bin/env bash
# This script groups visitors by IP and HTTP status code and displays occurrences in descending order

awk '{print $1, $9}' apache-access.log | sort | uniq -c | sort -rn
```

**Usage:**
```
$ ./8-for_ls | head -n 5
188 124.19.126.18 301
183 144.217.74.156 200
166 81.220.24.207 301
144 144.217.74.156 301
114 173.212.242.216 200
```

---

## Requirements

- All scripts are interpreted on Ubuntu 20.04 LTS
- All scripts must be executable (`chmod +x script-name`)
- The first line of every script is `#!/usr/bin/env bash`
- The second line of every script is a comment describing what it does

## Author
RyanGakire
