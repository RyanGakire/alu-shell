# Processes and Signals

A collection of Bash scripts for managing Linux processes and signals.

## Scripts

### `0-what-is-my-pid`
Displays the PID of the current script using the `$$` special variable.

### `1-list_your_processes`
Displays a list of all currently running processes for all users, including those without a TTY, in a user-oriented format with process hierarchy using `ps auxf`.

### `2-show_your_bash_pid`
Displays lines containing the word `bash` from the running process list, allowing you to easily identify the PID of your Bash process. Uses `ps auxf | grep bash`.

### `3-show_your_bash_pid_made_easy`
Displays the PID and process name of processes whose name contains the word `bash`, using `pgrep -l` (without `ps`).

### `4-to_infinity_and_beyond`
Displays `To infinity and beyond` indefinitely with a 2-second pause between each iteration using a `while true` loop and `sleep 2`.

### `5-dont_stop_me_now`
Stops the `4-to_infinity_and_beyond` process using `kill` and `pgrep` to find the PID dynamically.

### `6-stop_me_if_you_can`
Stops the `4-to_infinity_and_beyond` process using `pkill` (without `kill` or `killall`).

### `7-highlander`
Displays `To infinity and beyond` indefinitely with a 2-second pause. Displays `I am invincible!!!` when receiving a `SIGTERM` signal, using `trap` to intercept it and keep the process alive.

### `67-stop_me_if_you_can`
Stops the `7-highlander` process using `pkill`. A copy of `6-stop_me_if_you_can` adapted to target `7-highlander`.

### `8-beheaded_process`
Kills the `7-highlander` process using `pkill`.

### `10-process_and_pid_file`
- Creates `/var/run/myscript.pid` containing its own PID
- Displays `To infinity and beyond` indefinitely
- Displays `I hate the kill command` when receiving `SIGTERM`
- Displays `Y U no love me?!` when receiving `SIGINT`
- Deletes the PID file and exits cleanly when receiving `SIGQUIT` or `SIGTERM`

### `manage_my_process`
Indefinitely writes `I am alive!` to `/tmp/my_process` with a 2-second pause between each message. Meant to be managed by `11-manage_my_process`.

### `11-manage_my_process`
Init-style script that manages the `manage_my_process` script. Accepts the following arguments:

| Argument | Behavior |
|----------|----------|
| `start` | Starts `manage_my_process`, creates `/var/run/my_process.pid`, displays `manage_my_process started` |
| `stop` | Stops `manage_my_process`, deletes `/var/run/my_process.pid`, displays `manage_my_process stopped` |
| `restart` | Stops then restarts `manage_my_process`, recreates the PID file, displays `manage_my_process restarted` |
| anything else | Displays `Usage: manage_my_process {start|stop|restart}` |
