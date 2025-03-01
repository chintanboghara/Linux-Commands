# Linux Commands Documentation

## Table of Contents

1. [File Management Commands](#file-management-commands)
2. [File Permission Commands](#file-permission-commands)
3. [File Compression and Archiving Commands](#file-compression-and-archiving-commands)
4. [Process Management Commands](#process-management-commands)
5. [System Information Commands](#system-information-commands)
6. [Networking Commands](#networking-commands)
7. [IO Redirection](#io-redirection)
8. [Environment Variable Commands](#environment-variable-commands)
9. [User Management Commands](#user-management-commands)
10. [Shell Commands](#shell-commands)
11. [Scheduling Commands](#scheduling-commands)
12. [Text Processing Commands](#text-processing-commands)
13. [General Commands](#general-commands)
14. [System Control Commands](#system-control-commands)
15. [Bash Shortcuts](#bash-shortcuts)
16. [Nano Shortcuts](#nano-shortcuts)
17. [VI Shortcuts](#vi-shortcuts)
18. [Vim Shortcuts](#vim-shortcuts)
19. [Package Management Commands](#package-management-commands)
20. [Disk Space Usage & Monitoring](#disk-space-usage--monitoring)
21. [Partition & Filesystem Management](#partition--filesystem-management)
22. [Mounting & Unmounting Filesystems](#mounting--unmounting-filesystems)
23. [Disk Performance & Health Monitoring](#disk-performance--health-monitoring)
24. [Managing Disk Quotas](#managing-disk-quotas)
25. [LVM (Logical Volume Management)](#lvm-logical-volume-management)
26. [Swap Space Management](#swap-space-management)
27. [Secure Disk Erasing](#secure-disk-erasing)

---

## File Management Commands

### `ls`
- **Description**: List files and directories in the current directory.
- **Detailed Explanation**: Displays the contents of the current directory. Options like `-l` (long format), `-a` (show hidden files), and `-h` (human-readable sizes) enhance its functionality.
- **Example**:
  ```bash
  ls -la
  ```
  Lists all files (including hidden ones) in long format.

### `cd`
- **Description**: Change directory.
- **Detailed Explanation**: Navigates to a specified directory. Use `cd ..` to move up one level or `cd ~` to return to the home directory.
- **Example**:
  ```bash
  cd /var/www
  ```

### `pwd`
- **Description**: Print current working directory.
- **Detailed Explanation**: Outputs the full path of the current directory.
- **Example**:
  ```bash
  pwd
  ```
  Might output `/home/user`.

### `mkdir`
- **Description**: Create a new directory.
- **Detailed Explanation**: Creates directories with specified names. Use `-p` to create parent directories as needed.
- **Example**:
  ```bash
  mkdir -p project/src
  ```

### `rm`
- **Description**: Remove files and directories.
- **Detailed Explanation**: Deletes files or directories. Use `-r` for recursive deletion (directories) and `-f` to force without prompting.
- **Warning**: Permanently deletes files; use with caution.
- **Example**:
  ```bash
  rm -rf temp_folder
  ```

### `cp`
- **Description**: Copy files and directories.
- **Detailed Explanation**: Copies files or directories from source to destination. Use `-r` for directories.
- **Example**:
  ```bash
  cp -r docs /backup
  ```

### `mv`
- **Description**: Move or rename files and directories.
- **Detailed Explanation**: Moves files to a new location or renames them if the destination is a new name in the same directory.
- **Example**:
  ```bash
  mv file.txt docs/file.txt
  mv oldname.txt newname.txt
  ```

### `touch`
- **Description**: Create an empty file or update file timestamps.
- **Detailed Explanation**: Creates a new empty file if it doesn’t exist or updates the timestamp of an existing file.
- **Example**:
  ```bash
  touch notes.txt
  ```

### `cat`
- **Description**: Display the contents of a file.
- **Detailed Explanation**: Outputs file contents to the terminal. Can concatenate multiple files with `cat file1 file2`.
- **Example**:
  ```bash
  cat /etc/hosts
  ```

### `head`
- **Description**: Display the first few lines of a file.
- **Detailed Explanation**: Shows the first 10 lines by default. Use `-n` to specify a different number.
- **Example**:
  ```bash
  head -n 3 log.txt
  ```

### `tail`
- **Description**: Display the last few lines of a file.
- **Detailed Explanation**: Shows the last 10 lines by default. Use `-n` for a custom number or `-f` to follow updates.
- **Example**:
  ```bash
  tail -f /var/log/syslog
  ```

### `ln`
- **Description**: Create links between files.
- **Detailed Explanation**: Creates hard or symbolic (`-s`) links. Symbolic links point to another file’s path.
- **Example**:
  ```bash
  ln -s /usr/bin/python3 python
  ```

### `find`
- **Description**: Search for files and directories.
- **Detailed Explanation**: Searches based on criteria like name, type, or size. Powerful but slower than `locate`.
- **Example**:
  ```bash
  find / -name "*.conf"
  ```

### `locate`
- **Description**: Find files by name.
- **Detailed Explanation**: Uses a pre-built database for fast searches. Requires `updatedb` to refresh the database.
- **Example**:
  ```bash
  locate passwd
  ```

### `updatedb`
- **Description**: Update the file database used by `locate`.
- **Detailed Explanation**: Refreshes the database for `locate`. Requires root privileges.
- **Example**:
  ```bash
  sudo updatedb
  ```

---

## File Permission Commands

### `chmod`
- **Description**: Change file permissions.
- **Detailed Explanation**: Modifies read (`r`), write (`w`), and execute (`x`) permissions using numeric (e.g., 755) or symbolic (e.g., `u+x`) notation.
- **Example**:
  ```bash
  chmod 644 file.txt
  ```

### `chown`
- **Description**: Change file ownership.
- **Detailed Explanation**: Assigns a new owner and/or group to files. Use `user:group` syntax.
- **Example**:
  ```bash
  sudo chown apache:apache /var/www
  ```

### `chgrp`
- **Description**: Change group ownership.
- **Detailed Explanation**: Changes only the group ownership of a file or directory.
- **Example**:
  ```bash
  chgrp developers project
  ```

### `umask`
- **Description**: Set default file permissions.
- **Detailed Explanation**: Defines permissions subtracted from 666 (files) or 777 (directories) for new files. E.g., `022` sets 644 for files.
- **Example**:
  ```bash
  umask 022
  ```

---

## File Compression and Archiving Commands

### `tar`
- **Description**: Create or extract archive files.
- **Detailed Explanation**: Archives files into a `.tar` file. Use `-c` (create), `-x` (extract), `-z` (gzip), `-f` (file).
- **Example**:
  ```bash
  tar -czvf backup.tar.gz /home/user
  tar -xzvf backup.tar.gz
  ```

### `gzip`
- **Description**: Compress files.
- **Detailed Explanation**: Compresses a file, replacing it with a `.gz` version.
- **Example**:
  ```bash
  gzip largefile.txt
  ```

### `gunzip`
- **Description**: Decompress files compressed with `gzip`.
- **Detailed Explanation**: Restores the original file from a `.gz` archive.
- **Example**:
  ```bash
  gunzip largefile.txt.gz
  ```

### `zip`
- **Description**: Create compressed zip archives.
- **Detailed Explanation**: Combines and compresses files into a `.zip` file.
- **Example**:
  ```bash
  zip archive.zip file1 file2
  ```

### `unzip`
- **Description**: Extract files from a zip archive.
- **Detailed Explanation**: Decompresses and extracts contents of a `.zip` file.
- **Example**:
  ```bash
  unzip archive.zip
  ```

---

## Process Management Commands

### `ps`
- **Description**: Display running processes.
- **Detailed Explanation**: Shows process details. Use `-aux` for all processes with user info.
- **Example**:
  ```bash
  ps aux | grep nginx
  ```

### `top`
- **Description**: Monitor system processes in real-time.
- **Detailed Explanation**: Displays a dynamic view of CPU, memory, and process usage.
- **Example**:
  ```bash
  top
  ```

### `kill`
- **Description**: Terminate a process.
- **Detailed Explanation**: Sends a signal (default: TERM) to a process by PID. Use `-9` for forceful termination.
- **Example**:
  ```bash
  kill -9 12345
  ```

### `pkill`
- **Description**: Terminate processes based on their name.
- **Detailed Explanation**: Kills processes matching a name pattern.
- **Example**:
  ```bash
  pkill -u user
  ```

### `pgrep`
- **Description**: List processes based on their name.
- **Detailed Explanation**: Returns PIDs of processes matching a name.
- **Example**:
  ```bash
  pgrep python
  ```

### `nohup`
- **Description**: Run a command immune to hangups.
- **Detailed Explanation**: Allows a process to continue after logout. Use `&` to run in the background.
- **Example**:
  ```bash
  nohup python script.py &
  ```

---

## System Information Commands

### `uname`
- **Description**: Print system information.
- **Detailed Explanation**: Displays kernel and system details. Use `-a` for all info.
- **Example**:
  ```bash
  uname -a
  ```

### `whoami`
- **Description**: Display current username.
- **Detailed Explanation**: Shows the effective username of the current user.
- **Example**:
  ```bash
  whoami
  ```

### `free`
- **Description**: Display memory usage information.
- **Detailed Explanation**: Shows total, used, and free memory. Use `-h` for human-readable output.
- **Example**:
  ```bash
  free -h
  ```

### `uptime`
- **Description**: Show system uptime.
- **Detailed Explanation**: Displays how long the system has been running, plus load averages.
- **Example**:
  ```bash
  uptime
  ```

### `lscpu`
- **Description**: Display CPU information.
- **Detailed Explanation**: Lists CPU architecture, cores, and other details.
- **Example**:
  ```bash
  lscpu
  ```

### `lspci`
- **Description**: List PCI devices.
- **Detailed Explanation**: Shows PCI hardware like graphics cards and network adapters.
- **Example**:
  ```bash
  lspci
  ```

### `lsusb`
- **Description**: List USB devices.
- **Detailed Explanation**: Displays connected USB devices.
- **Example**:
  ```bash
  lsusb
  ```

### `lsof`
- **Description**: List open files and processes.
- **Detailed Explanation**: Shows files opened by processes, useful for troubleshooting.
- **Example**:
  ```bash
  lsof -i :80
  ```

### `lshw`
- **Description**: Display detailed hardware configuration.
- **Detailed Explanation**: Provides a comprehensive hardware report. Requires root privileges for full details.
- **Example**:
  ```bash
  sudo lshw
  ```

### `sar`
- **Description**: Collect and report system activity information.
- **Detailed Explanation**: Part of `sysstat`, monitors CPU, memory, and I/O. Use `-u` for CPU stats.
- **Example**:
  ```bash
  sar -u 1 5
  ```

### `date`
- **Description**: Display or set the system date and time.
- **Detailed Explanation**: Shows current date/time or sets it with a string (requires root).
- **Example**:
  ```bash
  date
  sudo date -s "2023-10-01 12:00"
  ```

### `cal`
- **Description**: Display a calendar.
- **Detailed Explanation**: Shows a month’s calendar. Use `-y` for the full year.
- **Example**:
  ```bash
  cal -y
  ```

---

## Networking Commands

### `ipconfig` *(Windows, not Linux)*
- **Description**: Display network interface information (Windows).
- **Detailed Explanation**: Included here for reference, but not a Linux command. Use `ifconfig` or `ip addr` on Linux.
- **Example** (Windows):
  ```cmd
  ipconfig
  ```

### `ifconfig`
- **Description**: Display network interface information (Linux/Unix).
- **Detailed Explanation**: Shows network interface details. Deprecated; prefer `ip addr`.
- **Example**:
  ```bash
  ifconfig
  ```

### `ip addr`
- **Description**: Show IP addresses and network interfaces (modern Linux).
- **Detailed Explanation**: Part of `iproute2`, displays and manages network configurations.
- **Example**:
  ```bash
  ip addr show
  ```

### `ping`
- **Description**: Send ICMP echo requests to a host.
- **Detailed Explanation**: Tests network connectivity. Use `-c` to limit packet count.
- **Example**:
  ```bash
  ping -c 4 google.com
  ```

### `netstat`
- **Description**: Display network connections and statistics.
- **Detailed Explanation**: Shows connections, ports, and routing. Use `-tuln` for listening ports.
- **Example**:
  ```bash
  netstat -tuln
  ```

### `ss`
- **Description**: Display network socket information.
- **Detailed Explanation**: Modern replacement for `netstat`, faster and more detailed.
- **Example**:
  ```bash
  ss -tuln
  ```

### `ssh`
- **Description**: Securely connect to a remote server.
- **Detailed Explanation**: Uses SSH protocol for secure remote access.
- **Example**:
  ```bash
  ssh user@192.168.1.10
  ```

### `scp`
- **Description**: Securely copy files between hosts.
- **Detailed Explanation**: Transfers files over SSH securely.
- **Example**:
  ```bash
  scp file.txt user@remote:/home/user/
  ```

### `wget`
- **Description**: Download files from the web.
- **Detailed Explanation**: Non-interactive tool for downloading files via HTTP/HTTPS/FTP.
- **Example**:
  ```bash
  wget https://example.com/file.zip
  ```

### `curl`
- **Description**: Transfer data to or from a server.
- **Detailed Explanation**: Supports multiple protocols; use `-O` to save files, `-X` for custom requests.
- **Example**:
  ```bash
  curl -O https://example.com/file.zip
  ```

### `rsync`
- **Description**: Synchronize files and directories between systems.
- **Detailed Explanation**: Efficiently syncs files, preserving permissions and timestamps.
- **Example**:
  ```bash
  rsync -avz /src user@remote:/dest
  ```

### `iftop`
- **Description**: Display network bandwidth usage.
- **Detailed Explanation**: Shows real-time bandwidth usage by connection.
- **Example**:
  ```bash
  sudo iftop
  ```

### `nc`
- **Description**: Netcat utility for network connections.
- **Detailed Explanation**: Versatile tool for TCP/UDP connections, often called the “Swiss Army knife” of networking.
- **Example**:
  ```bash
  nc -l 12345
  ```

### `iptables`
- **Description**: Administration tool for IPv4 packet filtering and NAT.
- **Detailed Explanation**: Configures firewall rules. Use `-L` to list rules.
- **Example**:
  ```bash
  sudo iptables -L
  ```

### `route`
- **Description**: Display or manipulate the IP routing table.
- **Detailed Explanation**: Shows or modifies routing. Use `-n` for numeric output.
- **Example**:
  ```bash
  route -n
  ```

### `ssh-keygen`
- **Description**: Generate SSH key pairs.
- **Detailed Explanation**: Creates public/private keys for SSH authentication.
- **Example**:
  ```bash
  ssh-keygen -t rsa -b 4096
  ```

---

## IO Redirection

### `cmd < file`
- **Description**: Input of `cmd` is taken from `file`.
- **Detailed Explanation**: Redirects file contents as input to a command.
- **Example**:
  ```bash
  wc -l < data.txt
  ```

### `cmd > file`
- **Description**: Standard output of `cmd` is redirected to `file`.
- **Detailed Explanation**: Overwrites `file` with command output.
- **Example**:
  ```bash
  ls > dirlist.txt
  ```

### `cmd 2> file`
- **Description**: Error output of `cmd` is redirected to `file`.
- **Detailed Explanation**: Captures stderr separately.
- **Example**:
  ```bash
  ls /nonexistent 2> errors.log
  ```

### `cmd &> file`
- **Description**: Every output of `cmd` is redirected to `file`.
- **Detailed Explanation**: Combines stdout and stderr into one file.
- **Example**:
  ```bash
  make &> build.log
  ```

### `cmd >> file`
- **Description**: Append the stdout of `cmd` to `file`.
- **Detailed Explanation**: Adds output to the end of `file` without overwriting.
- **Example**:
  ```bash
  echo "Log entry" >> logfile.txt
  ```

### `tee`
- **Description**: Redirect output to multiple files or processes.
- **Detailed Explanation**: Writes output to both a file and stdout. Use `-a` to append.
- **Example**:
  ```bash
  ls | tee output.txt
  ```

---

## Environment Variable Commands

### `export VARIABLE_NAME=value`
- **Description**: Set an environment variable.
- **Detailed Explanation**: Makes a variable available to the shell and subprocesses.
- **Example**:
  ```bash
  export MY_VAR="Hello"
  ```

### `echo $VARIABLE_NAME`
- **Description**: Display an environment variable’s value.
- **Detailed Explanation**: Prints the value of a variable.
- **Example**:
  ```bash
  echo $PATH
  ```

### `env`
- **Description**: List all environment variables.
- **Detailed Explanation**: Displays the current environment.
- **Example**:
  ```bash
  env
  ```

### `unset VARIABLE_NAME`
- **Description**: Remove an environment variable.
- **Detailed Explanation**: Deletes a variable from the environment.
- **Example**:
  ```bash
  unset MY_VAR
  ```

---

## User Management Commands

### `who`
- **Description**: Show who is currently logged in.
- **Detailed Explanation**: Lists active users and their login details.
- **Example**:
  ```bash
  who
  ```

### `sudo adduser username`
- **Description**: Create a new user account.
- **Detailed Explanation**: Prompts for user details like password and full name.
- **Example**:
  ```bash
  sudo adduser newuser
  ```

### `finger`
- **Description**: Display information about users.
- **Detailed Explanation**: Shows user details like login time and home directory (if installed).
- **Example**:
  ```bash
  finger newuser
  ```

### `sudo deluser USER GROUPNAME`
- **Description**: Remove a user from a group.
- **Detailed Explanation**: Removes a user from a specified group, not the system.
- **Example**:
  ```bash
  sudo deluser newuser sudo
  ```

### `last`
- **Description**: Show recent login history.
- **Detailed Explanation**: Displays past logins from `/var/log/wtmp`.
- **Example**:
  ```bash
  last
  ```

### `sudo userdel -r username`
- **Description**: Delete a user account and files.
- **Detailed Explanation**: Removes a user and their home directory with `-r`.
- **Example**:
  ```bash
  sudo userdel -r olduser
  ```

### `sudo passwd -l username`
- **Description**: Lock a user account.
- **Detailed Explanation**: Disables login by locking the password.
- **Example**:
  ```bash
  sudo passwd -l newuser
  ```

### `su - username`
- **Description**: Switch to another user account.
- **Detailed Explanation**: Starts a shell as another user. Use `-` for their environment.
- **Example**:
  ```bash
  su - newuser
  ```

### `sudo usermod -a -G GROUPNAME USERNAME`
- **Description**: Add a user to a group.
- **Detailed Explanation**: Appends (`-a`) a user to a group (`-G`).
- **Example**:
  ```bash
  sudo usermod -a -G developers newuser
  ```

---

## Shell Commands

### `alias`
- **Description**: Create an alias for a command.
- **Detailed Explanation**: Shortens commands for the current session. Add to `.bashrc` for persistence.
- **Example**:
  ```bash
  alias ll="ls -l"
  ```

### `source`
- **Description**: Execute commands from a file in the current shell.
- **Detailed Explanation**: Runs a script in the current environment (alias: `.`).
- **Example**:
  ```bash
  source ~/.bashrc
  ```

### `history`
- **Description**: Display the command history.
- **Detailed Explanation**: Lists previously executed commands.
- **Example**:
  ```bash
  history
  ```

---

## Scheduling Commands

### `crontab`
- **Description**: Schedule commands or scripts to run periodically.
- **Detailed Explanation**: Manages cron jobs. Use `-e` to edit, `-l` to list.
- **Example**:
  ```bash
  crontab -e
  ```
  Add: `0 1 * * * backup.sh` to run daily at 1 AM.

---

## Text Processing Commands

### `grep`
- **Description**: Search for patterns in text.
- **Detailed Explanation**: Finds lines matching a pattern. Use `-r` for recursive search.
- **Example**:
  ```bash
  grep -r "error" /var/log
  ```

### `awk`
- **Description**: Text processing tool for data extraction and manipulation.
- **Detailed Explanation**: Processes text by fields and patterns.
- **Example**:
  ```bash
  awk '{print $1}' access.log
  ```

### `sed`
- **Description**: Stream editor for text manipulation.
- **Detailed Explanation**: Edits text streams. Use `s/pattern/replace/` for substitution.
- **Example**:
  ```bash
  sed 's/foo/bar/g' file.txt
  ```

### `diff`
- **Description**: Compare files line by line.
- **Detailed Explanation**: Highlights differences between two files.
- **Example**:
  ```bash
  diff file1.txt file2.txt
  ```

### `sort`
- **Description**: Sort lines of text files.
- **Detailed Explanation**: Orders lines alphabetically or numerically with `-n`.
- **Example**:
  ```bash
  sort -n numbers.txt
  ```

### `cut`
- **Description**: Extract sections from lines of files.
- **Detailed Explanation**: Cuts fields by delimiter (`-d`) and field number (`-f`).
- **Example**:
  ```bash
  cut -d',' -f2 data.csv
  ```

### `wc`
- **Description**: Count lines, words, and characters in a file.
- **Detailed Explanation**: Use `-l` (lines), `-w` (words), `-c` (characters).
- **Example**:
  ```bash
  wc -l script.sh
  ```

---

## General Commands

### `man`
- **Description**: Display the manual pages for a command.
- **Detailed Explanation**: Provides detailed documentation for commands.
- **Example**:
  ```bash
  man grep
  ```

### `which`
- **Description**: Display the location of a command.
- **Detailed Explanation**: Shows the full path to an executable.
- **Example**:
  ```bash
  which bash
  ```

### `sudo`
- **Description**: Run a command with administrative privileges.
- **Detailed Explanation**: Executes commands as root or another user.
- **Example**:
  ```bash
  sudo apt update
  ```

---

## System Control Commands

### `shutdown`
- **Description**: Shut down or reboot the system.
- **Detailed Explanation**: Use `-h` to halt, `-r` to reboot, and a time argument.
- **Example**:
  ```bash
  sudo shutdown -r now
  ```

### `reboot`
- **Description**: Reboot the system.
- **Detailed Explanation**: Immediately restarts the system.
- **Example**:
  ```bash
  sudo reboot
  ```

### `halt`
- **Description**: Halt the system.
- **Detailed Explanation**: Stops all processes and powers off (use with caution).
- **Example**:
  ```bash
  sudo halt
  ```

---

## Bash Shortcuts

- **Ctrl + A**: Move to the beginning of the line.
- **Ctrl + E**: Move to the end of the line.
- **Ctrl + B**: Move back one character.
- **Ctrl + F**: Move forward one character.
- **Alt + B**: Move back one word.
- **Alt + F**: Move forward one word.
- **Ctrl + U**: Cut from cursor to beginning of line.
- **Ctrl + K**: Cut from cursor to end of line.
- **Ctrl + W**: Cut the word before the cursor.
- **Ctrl + Y**: Paste the last cut text.
- **Ctrl + L**: Clear the screen.
- **Ctrl + R**: Search command history (type to search, Enter to execute).
- **Ctrl + G**: Exit history search mode.
- **Ctrl + P**: Previous command in history.
- **Ctrl + N**: Next command in history.
- **Ctrl + C**: Terminate the current command.

---

## Nano Shortcuts

- **Ctrl + O**: Save the file (write out).
- **Ctrl + X**: Exit Nano.
- **Ctrl + R**: Read a file into the current buffer.
- **Ctrl + J**: Justify the current paragraph.
- **Ctrl + Y**: Scroll up one page.
- **Ctrl + V**: Scroll down one page.
- **Alt + \\**: Go to a specific line number.
- **Alt + ,**: Go to the beginning of the current line.
- **Alt + .**: Go to the end of the current line.
- **Ctrl + K**: Cut from cursor to end of line.
- **Ctrl + U**: Uncut (paste) the last cut text.
- **Ctrl + 6**: Mark a block of text (start selection).
- **Ctrl + W**: Search for a string.
- **Alt + W**: Search and replace a string.
- **Alt + R**: Repeat the last search.

---

## VI Shortcuts

- **cw**: Change the current word (delete and enter insert mode).
- **dd**: Delete the current line.
- **x**: Delete the character under the cursor.
- **R**: Enter replace mode (overwrite text).
- **o**: Insert a new line below and enter insert mode.
- **u**: Undo the last change.
- **s**: Substitute the character under the cursor (delete and insert).
- **dw**: Delete from cursor to start of next word.
- **D**: Delete from cursor to end of line.
- **4dw**: Delete the next four words.
- **A**: Append at the end of the line.
- **S**: Delete the current line and enter insert mode.
- **r**: Replace the character under the cursor.
- **i**: Insert before the cursor.
- **3dd**: Delete three lines.
- **ESC**: Exit insert mode to command mode.
- **U**: Undo all changes on the current line.
- **~**: Toggle case of the character under the cursor.
- **a**: Append after the cursor.
- **C**: Change from cursor to end of line (delete and insert).

---

## Vim Shortcuts

- **i**: Enter insert mode before the cursor.
- **x**: Delete the character under the cursor.
- **dd**: Delete the current line.
- **yy**: Copy (yank) the current line.
- **p**: Paste below the current line.
- **u**: Undo the last change.
- **Ctrl + R**: Redo the last undone change.
- **:w**: Save the file.
- **:q**: Quit Vim.
- **:wq**: Save and quit.
- **:q!**: Quit without saving.
- **:set nu**: Display line numbers.
- **v**: Enter visual mode (select text).
- **y**: Copy the selected text.
- **d**: Delete the selected text.
- **p**: Paste the copied or deleted text.
- **:s/old/new/g**: Replace all occurrences of "old" with "new" in the current line.

---

## Package Management Commands

### `apt update`
- **Description**: Update package list (Debian/Ubuntu).
- **Detailed Explanation**: Refreshes the local package index.
- **Example**:
  ```bash
  sudo apt update
  ```

### `apt upgrade`
- **Description**: Upgrade installed packages (Debian/Ubuntu).
- **Detailed Explanation**: Updates all installed packages to their latest versions.
- **Example**:
  ```bash
  sudo apt upgrade
  ```

### `apt install package_name`
- **Description**: Install a package (Debian/Ubuntu).
- **Detailed Explanation**: Installs a specified package and its dependencies.
- **Example**:
  ```bash
  sudo apt install nginx
  ```

### `apt remove package_name`
- **Description**: Remove a package (Debian/Ubuntu).
- **Detailed Explanation**: Uninstalls a package, leaving configuration files.
- **Example**:
  ```bash
  sudo apt remove nginx
  ```

### `apt search pattern`
- **Description**: Search for packages (Debian/Ubuntu).
- **Detailed Explanation**: Finds packages matching a keyword.
- **Example**:
  ```bash
  apt search python
  ```

### `apt list --installed`
- **Description**: List installed packages (Debian/Ubuntu).
- **Detailed Explanation**: Shows all currently installed packages.
- **Example**:
  ```bash
  apt list --installed
  ```

### `dpkg -i package.deb`
- **Description**: Install a .deb package file (Debian/Ubuntu).
- **Detailed Explanation**: Installs a local `.deb` file manually.
- **Example**:
  ```bash
  sudo dpkg -i package.deb
  ```

### `yum update`
- **Description**: Update packages on RPM-based systems (e.g., CentOS).
- **Detailed Explanation**: Updates all packages (older RPM systems).
- **Example**:
  ```bash
  sudo yum update
  ```

### `yum install package_name`
- **Description**: Install package on RPM systems.
- **Detailed Explanation**: Installs a package and dependencies.
- **Example**:
  ```bash
  sudo yum install httpd
  ```

### `dnf search term`
- **Description**: Search for packages using DNF (Fedora).
- **Detailed Explanation**: Searches package repositories (modern RPM replacement).
- **Example**:
  ```bash
  dnf search vim
  ```

### `pacman -S package_name`
- **Description**: Install package on Arch Linux.
- **Detailed Explanation**: Installs a package and its dependencies.
- **Example**:
  ```bash
  sudo pacman -S vim
  ```

### `pacman -Syu`
- **Description**: Update Arch Linux system.
- **Detailed Explanation**: Synchronizes and updates all packages.
- **Example**:
  ```bash
  sudo pacman -Syu
  ```

---

## Disk Space Usage & Monitoring

### `df -h`
- **Description**: Show disk space usage in human-readable format.
- **Detailed Explanation**: Displays used and available space on mounted filesystems.
- **Example**:
  ```bash
  df -h
  ```

### `du -sh /var/log`
- **Description**: Show size of a specific directory.
- **Detailed Explanation**: Summarizes total size (`-s`) in human-readable format (`-h`).
- **Example**:
  ```bash
  du -sh /var/log
  ```

### `du -h --max-depth=1`
- **Description**: Show sizes of subdirectories (1 level deep).
- **Detailed Explanation**: Lists sizes of directories at one level.
- **Example**:
  ```bash
  du -h --max-depth=1 /home
  ```

### `lsblk`
- **Description**: Display information about block devices (partitions & disks).
- **Detailed Explanation**: Shows device hierarchy and mount points.
- **Example**:
  ```bash
  lsblk
  ```

### `blkid`
- **Description**: Show UUID and filesystem type of partitions.
- **Detailed Explanation**: Identifies partition details for mounting.
- **Example**:
  ```bash
  sudo blkid
  ```

### `findmnt`
- **Description**: Display mounted filesystems.
- **Detailed Explanation**: Lists mounted filesystems and their properties.
- **Example**:
  ```bash
  findmnt
  ```

### `mount | column -t`
- **Description**: List mounted files in a readable table format.
- **Detailed Explanation**: Pipes `mount` output to `column` for alignment.
- **Example**:
  ```bash
  mount | column -t
  ```

---

## Partition & Filesystem Management

### `fdisk -l`
- **Description**: Show partition table of all disks.
- **Detailed Explanation**: Lists partitions (requires root).
- **Example**:
  ```bash
  sudo fdisk -l
  ```

### `parted -l`
- **Description**: Display partition details using GNU Parted.
- **Detailed Explanation**: Shows partition info and disk layout.
- **Example**:
  ```bash
  sudo parted -l
  ```

### `mkfs.ext4 /dev/sdb1`
- **Description**: Format a partition with ext4 filesystem.
- **Detailed Explanation**: Creates an ext4 filesystem, erasing all data.
- **Warning**: Destroys existing data on the partition.
- **Example**:
  ```bash
  sudo mkfs.ext4 /dev/sdb1
  ```

### `mkfs.xfs /dev/sdb1`
- **Description**: Format a partition with XFS filesystem.
- **Detailed Explanation**: Creates an XFS filesystem, erasing all data.
- **Warning**: Destroys existing data.
- **Example**:
  ```bash
  sudo mkfs.xfs /dev/sdb1
  ```

### `e2fsck -f /dev/sdb1`
- **Description**: Check and repair an ext4 filesystem.
- **Detailed Explanation**: Forces a filesystem check (`-f`).
- **Example**:
  ```bash
  sudo e2fsck -f /dev/sdb1
  ```

### `xfs_repair /dev/sdb1`
- **Description**: Repair an XFS filesystem.
- **Detailed Explanation**: Fixes inconsistencies in XFS filesystems.
- **Example**:
  ```bash
  sudo xfs_repair /dev/sdb1
  ```

### `tune2fs -m 5 /dev/sdb1`
- **Description**: Set reserved space on ext4 filesystem (5% in this case).
- **Detailed Explanation**: Reserves space for root use.
- **Example**:
  ```bash
  sudo tune2fs -m 5 /dev/sdb1
  ```

---

## Mounting & Unmounting Filesystems

### `mount /dev/sdb1 /mnt`
- **Description**: Mount a partition to `/mnt`.
- **Detailed Explanation**: Attaches a filesystem to a directory.
- **Example**:
  ```bash
  sudo mount /dev/sdb1 /mnt
  ```

### `umount /mnt`
- **Description**: Unmount a filesystem from `/mnt`.
- **Detailed Explanation**: Detaches a mounted filesystem.
- **Example**:
  ```bash
  sudo umount /mnt
  ```

### `mount -o remount,rw /`
- **Description**: Remount root filesystem as read-write.
- **Detailed Explanation**: Changes mount options without unmounting.
- **Example**:
  ```bash
  sudo mount -o remount,rw /
  ```

### `mount -t nfs 192.168.1.100:/share /mnt`
- **Description**: Mount an NFS share.
- **Detailed Explanation**: Connects to a remote NFS server.
- **Example**:
  ```bash
  sudo mount -t nfs 192.168.1.100:/share /mnt
  ```

### `mount -o loop file.iso /mnt`
- **Description**: Mount an ISO file as a virtual disk.
- **Detailed Explanation**: Treats an ISO as a block device.
- **Example**:
  ```bash
  sudo mount -o loop disk.iso /mnt
  ```

---

## Disk Performance & Health Monitoring

### `iotop`
- **Description**: Show real-time disk I/O usage by processes.
- **Detailed Explanation**: Displays disk read/write activity per process.
- **Example**:
  ```bash
  sudo iotop
  ```

### `iostat -x 1`
- **Description**: Show detailed disk usage statistics.
- **Detailed Explanation**: Reports I/O stats every second (`1`).
- **Example**:
  ```bash
  iostat -x 1
  ```

### `smartctl -H /dev/sda`
- **Description**: Check SMART health status of a disk.
- **Detailed Explanation**: Verifies disk health via SMART data.
- **Example**:
  ```bash
  sudo smartctl -H /dev/sda
  ```

### `smartctl -a /dev/sda`
- **Description**: Display full SMART diagnostics.
- **Detailed Explanation**: Shows all SMART attributes.
- **Example**:
  ```bash
  sudo smartctl -a /dev/sda
  ```

### `badblocks -sv /dev/sdb`
- **Description**: Scan for bad sectors on a disk.
- **Detailed Explanation**: Verbose (`-v`) scan with output (`-s`).
- **Example**:
  ```bash
  sudo badblocks -sv /dev/sdb
  ```

---

## Managing Disk Quotas

### `quota -u username`
- **Description**: Show disk quota for a user.
- **Detailed Explanation**: Displays usage and limits for a user.
- **Example**:
  ```bash
  quota -u user1
  ```

### `edquota -u username`
- **Description**: Edit disk quota for a user.
- **Detailed Explanation**: Opens an editor to set quotas.
- **Example**:
  ```bash
  sudo edquota -u user1
  ```

### `repquota -a`
- **Description**: Show quota report for all users.
- **Detailed Explanation**: Summarizes quota usage system-wide.
- **Example**:
  ```bash
  sudo repquota -a
  ```

### `setquota -u username 500M 1G 0 0 /dev/sda1`
- **Description**: Set quota (500MB soft, 1GB hard).
- **Detailed Explanation**: Defines soft (warning) and hard (limit) quotas.
- **Example**:
  ```bash
  sudo setquota -u user1 500M 1G 0 0 /dev/sda1
  ```

---

## LVM (Logical Volume Management)

### `pvcreate /dev/sdb`
- **Description**: Initialize a physical volume for LVM.
- **Detailed Explanation**: Prepares a disk for LVM use.
- **Example**:
  ```bash
  sudo pvcreate /dev/sdb
  ```

### `vgcreate vg /dev/sdb`
- **Description**: Create a volume group from a physical volume.
- **Detailed Explanation**: Groups physical volumes into a volume group.
- **Example**:
  ```bash
  sudo vgcreate my_vg /dev/sdb
  ```

### `lvcreate -L 10G -n my_lv my_vg`
- **Description**: Create a 10GB logical volume.
- **Detailed Explanation**: Allocates space from a volume group.
- **Example**:
  ```bash
  sudo lvcreate -L 10G -n my_lv my_vg
  ```

### `lvextend -L +5G /dev/my_vg/my_lv`
- **Description**: Extend a logical volume by 5GB.
- **Detailed Explanation**: Increases the size of an existing LV.
- **Example**:
  ```bash
  sudo lvextend -L +5G /dev/my_vg/my_lv
  ```

### `resize2fs /dev/my_vg/my_lv`
- **Description**: Resize ext4 filesystem after extending LVM.
- **Detailed Explanation**: Adjusts the filesystem to the new LV size.
- **Example**:
  ```bash
  sudo resize2fs /dev/my_vg/my_lv
  ```

---

## Swap Space Management

### `swapon -s`
- **Description**: Show active swap partitions and files.
- **Detailed Explanation**: Lists current swap areas and usage.
- **Example**:
  ```bash
  swapon -s
  ```

### `free -m`
- **Description**: Display system memory usage including swap.
- **Detailed Explanation**: Shows memory and swap in megabytes.
- **Example**:
  ```bash
  free -m
  ```

### `mkswap /dev/sdb2`
- **Description**: Format a partition as swap.
- **Detailed Explanation**: Prepares a partition for swap use.
- **Example**:
  ```bash
  sudo mkswap /dev/sdb2
  ```

### `swapon /dev/sdb2`
- **Description**: Enable swap partition.
- **Detailed Explanation**: Activates a swap area.
- **Example**:
  ```bash
  sudo swapon /dev/sdb2
  ```

### `swapoff /dev/sdb2`
- **Description**: Disable swap partition.
- **Detailed Explanation**: Deactivates a swap area.
- **Example**:
  ```bash
  sudo swapoff /dev/sdb2
  ```

### `fallocate -l 2G /swapfile`
- **Description**: Create a 2GB swap file.
- **Detailed Explanation**: Allocates space for a file-based swap.
- **Example**:
  ```bash
  sudo fallocate -l 2G /swapfile
  ```

### `mkswap /swapfile`
- **Description**: Format swap file.
- **Detailed Explanation**: Sets up a file as swap space.
- **Example**:
  ```bash
  sudo mkswap /swapfile
  ```

### `swapon /swapfile`
- **Description**: Enable swap file.
- **Detailed Explanation**: Activates the swap file.
- **Example**:
  ```bash
  sudo swapon /swapfile
  ```

---

## Secure Disk Erasing

### `shred -n 3 -z /dev/sdb`
- **Description**: Securely erase a disk by overwriting it 3 times.
- **Detailed Explanation**: Overwrites data (`-n 3`) and zeros it (`-z`).
- **Example**:
  ```bash
  sudo shred -n 3 -z /dev/sdb
  ```

### `dd if=/dev/zero of=/dev/sdb bs=1M status=progress`
- **Description**: Wipe a disk by filling it with zeroes.
- **Detailed Explanation**: Writes zeros to the entire disk with progress.
- **Example**:
  ```bash
  sudo dd if=/dev/zero of=/dev/sdb bs=1M status=progress
  ```

### `wipe -rf /dev/sdb`
- **Description**: Securely wipe a disk (requires `wipe` utility).
- **Detailed Explanation**: Recursively (`-r`) and forcefully (`-f`) erases data.
- **Example**:
  ```bash
  sudo wipe -rf /dev/sdb
  ```
