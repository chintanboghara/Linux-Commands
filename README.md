# Linux Commands

### Table of Contents

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

## File Management Commands

### `ls`
- **Description**: List directory contents.
- **Explanation**: Shows files and directories. Options: `-l` (long format), `-a` (hidden files), `-h` (human-readable sizes).
- **Example**:
  ```bash
  ls -lah
  ```
  Lists all files with details and readable sizes.

### `cd`
- **Description**: Change directory.
- **Explanation**: Navigates directories. Use `cd ..` (parent), `cd ~` (home), `cd -` (previous).
- **Example**:
  ```bash
  cd /var/www
  ```

### `pwd`
- **Description**: Print working directory.
- **Explanation**: Displays the current directory’s full path.
- **Example**:
  ```bash
  pwd
  ```
  Outputs: `/home/user`.

### `mkdir`
- **Description**: Create directories.
- **Explanation**: Makes new directories; `-p` creates parents if needed.
- **Example**:
  ```bash
  mkdir -p project/src
  ```

### `rm`
- **Description**: Remove files or directories.
- **Explanation**: Deletes permanently. Use `-r` (recursive), `-f` (force). Caution: No undo.
- **Example**:
  ```bash
  rm -rf temp_folder
  ```

### `cp`
- **Description**: Copy files or directories.
- **Explanation**: Copies from source to destination; `-r` for directories.
- **Example**:
  ```bash
  cp -r docs /backup
  ```

### `mv`
- **Description**: Move or rename files/directories.
- **Explanation**: Moves or renames; destination determines action.
- **Example**:
  ```bash
  mv file.txt docs/file.txt
  mv oldname.txt newname.txt
  ```

### `touch`
- **Description**: Create empty files or update timestamps.
- **Explanation**: Creates files or refreshes timestamps if they exist.
- **Example**:
  ```bash
  touch notes.txt
  ```

### `cat`
- **Description**: Concatenate and display file contents.
- **Explanation**: Outputs file contents; can combine multiple files.
- **Example**:
  ```bash
  cat /etc/hosts
  ```

### `head`
- **Description**: Show the first lines of a file.
- **Explanation**: Defaults to 10 lines; `-n` sets custom count.
- **Example**:
  ```bash
  head -n 5 log.txt
  ```

### `tail`
- **Description**: Show the last lines of a file.
- **Explanation**: Defaults to 10 lines; `-n` for count, `-f` to follow.
- **Example**:
  ```bash
  tail -f /var/log/syslog
  ```

### `ln`
- **Description**: Create hard or symbolic links.
- **Explanation**: Links files; `-s` for symbolic links.
- **Example**:
  ```bash
  ln -s /usr/bin/python3 python
  ```

### `find`
- **Description**: Search for files/directories.
- **Explanation**: Searches by name, type, size; flexible but slower than `locate`.
- **Example**:
  ```bash
  find / -name "*.conf"
  ```

### `locate`
- **Description**: Quickly find files by name.
- **Explanation**: Uses a database (update with `updatedb`) for speed.
- **Example**:
  ```bash
  locate passwd
  ```

### `updatedb`
- **Description**: Update the `locate` database.
- **Explanation**: Refreshes the file index; needs root.
- **Example**:
  ```bash
  sudo updatedb
  ```

### `tree`
- **Description**: Display directory tree.
- **Explanation**: Shows structure; `-a` (all files), `-d` (dirs only).
- **Example**:
  ```bash
  tree -a /home/user
  ```

### `file`
- **Description**: Determine file type.
- **Explanation**: Identifies file type (e.g., text, binary).
- **Example**:
  ```bash
  file image.png
  ```

## File Permission Commands

### `chmod`
- **Description**: Change file permissions.
- **Explanation**: Sets read (`r`), write (`w`), execute (`x`) via numeric (e.g., 644) or symbolic (e.g., `u+x`) modes.
- **Example**:
  ```bash
  chmod 644 file.txt
  ```

### `chown`
- **Description**: Change file owner and group.
- **Explanation**: Assigns ownership; syntax `user:group`.
- **Example**:
  ```bash
  sudo chown apache:apache /var/www
  ```

### `chgrp`
- **Description**: Change group ownership.
- **Explanation**: Updates group ownership only.
- **Example**:
  ```bash
  chgrp developers project
  ```

### `umask`
- **Description**: Set default permissions for new files.
- **Explanation**: Subtracts from 666 (files) or 777 (dirs); `022` yields 644.
- **Example**:
  ```bash
  umask 022
  ```

### `getfacl`
- **Description**: Get file access control lists (ACLs).
- **Explanation**: Shows detailed permissions beyond `chmod`.
- **Example**:
  ```bash
  getfacl file.txt
  ```

### `setfacl`
- **Description**: Set file ACLs.
- **Explanation**: Grants specific permissions; `-m` modifies.
- **Example**:
  ```bash
  setfacl -m u:user:rw file.txt
  ```

## File Compression and Archiving Commands

### `tar`
- **Description**: Archive files.
- **Explanation**: Creates/extracts `.tar` files; `-c` (create), `-x` (extract), `-z` (gzip), `-f` (file).
- **Example**:
  ```bash
  tar -czvf backup.tar.gz /home/user
  tar -xzvf backup.tar.gz
  ```

### `gzip`
- **Description**: Compress files.
- **Explanation**: Creates `.gz` files, replacing originals.
- **Example**:
  ```bash
  gzip largefile.txt
  ```

### `gunzip`
- **Description**: Decompress `.gz` files.
- **Explanation**: Restores original files.
- **Example**:
  ```bash
  gunzip largefile.txt.gz
  ```

### `zip`
- **Description**: Create `.zip` archives.
- **Explanation**: Compresses files into `.zip`.
- **Example**:
  ```bash
  zip archive.zip file1 file2
  ```

### `unzip`
- **Description**: Extract `.zip` archives.
- **Explanation**: Decompresses and extracts `.zip` contents.
- **Example**:
  ```bash
  unzip archive.zip
  ```

### `bzip2`
- **Description**: Compress with bzip2.
- **Explanation**: Better compression than `gzip`; creates `.bz2`.
- **Example**:
  ```bash
  bzip2 largefile.txt
  ```

### `bunzip2`
- **Description**: Decompress `.bz2` files.
- **Explanation**: Restores original files from `.bz2`.
- **Example**:
  ```bash
  bunzip2 largefile.txt.bz2
  ```

### `xz`
- **Description**: Compress with xz.
- **Explanation**: High compression ratio; creates `.xz`.
- **Example**:
  ```bash
  xz largefile.txt
  ```

### `unxz`
- **Description**: Decompress `.xz` files.
- **Explanation**: Restores original files from `.xz`.
- **Example**:
  ```bash
  unxz largefile.txt.xz
  ```

## Process Management Commands

### `ps`
- **Description**: List running processes.
- **Explanation**: Shows process details; `-aux` for all with user info.
- **Example**:
  ```bash
  ps aux | grep nginx
  ```

### `top`
- **Description**: Monitor processes in real-time.
- **Explanation**: Displays CPU, memory, and process usage dynamically.
- **Example**:
  ```bash
  top
  ```

### `kill`
- **Description**: Terminate a process by PID.
- **Explanation**: Sends signals; `-9` (SIGKILL) forces termination.
- **Example**:
  ```bash
  kill -9 12345
  ```

### `pkill`
- **Description**: Kill processes by name.
- **Explanation**: Targets processes by name pattern.
- **Example**:
  ```bash
  pkill -u user
  ```

### `pgrep`
- **Description**: Find PIDs by name.
- **Explanation**: Lists PIDs matching a name.
- **Example**:
  ```bash
  pgrep python
  ```

### `nohup`
- **Description**: Run commands immune to hangups.
- **Explanation**: Persists after logout; `&` for background.
- **Example**:
  ```bash
  nohup python script.py &
  ```

### `htop`
- **Description**: Interactive process viewer.
- **Explanation**: Enhanced `top` alternative with a friendly UI.
- **Example**:
  ```bash
  htop
  ```

### `nice`
- **Description**: Set process priority.
- **Explanation**: Adjusts priority (-20 high to 19 low); default 0.
- **Example**:
  ```bash
  nice -n 10 tar -czf backup.tar.gz /home
  ```

### `renice`
- **Description**: Change priority of running processes.
- **Explanation**: Modifies priority by PID.
- **Example**:
  ```bash
  renice 15 -p 12345
  ```

### `jobs`
- **Description**: List background jobs.
- **Explanation**: Shows jobs in the current shell.
- **Example**:
  ```bash
  jobs
  ```

### `bg`
- **Description**: Resume job in background.
- **Explanation**: Continues a suspended job.
- **Example**:
  ```bash
  bg %1
  ```

### `fg`
- **Description**: Bring job to foreground.
- **Explanation**: Resumes a job in the foreground.
- **Example**:
  ```bash
  fg %1
  ```

## System Information Commands

### `uname`
- **Description**: Display system info.
- **Explanation**: Shows kernel details; `-a` for all.
- **Example**:
  ```bash
  uname -a
  ```

### `whoami`
- **Description**: Show current username.
- **Explanation**: Displays effective user.
- **Example**:
  ```bash
  whoami
  ```

### `free`
- **Description**: Show memory usage.
- **Explanation**: Lists total/used/free memory; `-h` for readable units.
- **Example**:
  ```bash
  free -h
  ```

### `uptime`
- **Description**: Show system uptime and load.
- **Explanation**: Displays runtime and load averages.
- **Example**:
  ```bash
  uptime
  ```

### `lscpu`
- **Description**: Display CPU info.
- **Explanation**: Shows CPU architecture and cores.
- **Example**:
  ```bash
  lscpu
  ```

### `lspci`
- **Description**: List PCI devices.
- **Explanation**: Shows PCI hardware (e.g., GPUs, NICs).
- **Example**:
  ```bash
  lspci
  ```

### `lsusb`
- **Description**: List USB devices.
- **Explanation**: Displays connected USB devices.
- **Example**:
  ```bash
  lsusb
  ```

### `lsof`
- **Description**: List open files.
- **Explanation**: Shows files/processes; useful for debugging.
- **Example**:
  ```bash
  lsof -i :80
  ```

### `lshw`
- **Description**: Show hardware details.
- **Explanation**: Full hardware report; needs root for all info.
- **Example**:
  ```bash
  sudo lshw
  ```

### `sar`
- **Description**: Monitor system activity.
- **Explanation**: Tracks CPU/memory/I/O (`sysstat`); `-u` for CPU.
- **Example**:
  ```bash
  sar -u 1 5
  ```

### `date`
- **Description**: Show/set date and time.
- **Explanation**: Displays or sets system time (root for set).
- **Example**:
  ```bash
  date
  sudo date -s "2023-10-01 12:00"
  ```

### `cal`
- **Description**: Display calendar.
- **Explanation**: Shows month; `-y` for year.
- **Example**:
  ```bash
  cal -y
  ```

### `hostname`
- **Description**: Show/set hostname.
- **Explanation**: Displays or changes system hostname.
- **Example**:
  ```bash
  hostname
  ```

### `dmidecode`
- **Description**: Show BIOS hardware info.
- **Explanation**: Detailed hardware data; needs root.
- **Example**:
  ```bash
  sudo dmidecode -t memory
  ```

## Networking Commands

### `ifconfig`
- **Description**: Show network interfaces (deprecated).
- **Explanation**: Displays network info; use `ip addr` instead.
- **Example**:
  ```bash
  ifconfig
  ```

### `ip addr`
- **Description**: Manage IP addresses/interfaces.
- **Explanation**: Modern `ifconfig` replacement (`iproute2`).
- **Example**:
  ```bash
  ip addr show
  ```

### `ping`
- **Description**: Test network connectivity.
- **Explanation**: Sends ICMP packets; `-c` limits count.
- **Example**:
  ```bash
  ping -c 4 google.com
  ```

### `netstat`
- **Description**: Show network stats.
- **Explanation**: Displays connections/ports; `-tuln` for listening.
- **Example**:
  ```bash
  netstat -tuln
  ```

### `ss`
- **Description**: Show socket info.
- **Explanation**: Faster `netstat` alternative.
- **Example**:
  ```bash
  ss -tuln
  ```

### `ssh`
- **Description**: Secure remote connection.
- **Explanation**: Connects via SSH protocol.
- **Example**:
  ```bash
  ssh user@192.168.1.10
  ```

### `scp`
- **Description**: Secure file copy.
- **Explanation**: Transfers files over SSH.
- **Example**:
  ```bash
  scp file.txt user@remote:/home/user/
  ```

### `wget`
- **Description**: Download files.
- **Explanation**: Non-interactive; supports HTTP/HTTPS/FTP.
- **Example**:
  ```bash
  wget https://example.com/file.zip
  ```

### `curl`
- **Description**: Transfer data with URLs.
- **Explanation**: Versatile; `-O` saves files.
- **Example**:
  ```bash
  curl -O https://example.com/file.zip
  ```

### `rsync`
- **Description**: Sync files between systems.
- **Explanation**: Efficient sync with permissions/timestamps.
- **Example**:
  ```bash
  rsync -avz /src user@remote:/dest
  ```

### `iftop`
- **Description**: Monitor bandwidth usage.
- **Explanation**: Real-time connection bandwidth.
- **Example**:
  ```bash
  sudo iftop
  ```

### `nc`
- **Description**: Network utility (Netcat).
- **Explanation**: TCP/UDP tool; versatile for debugging.
- **Example**:
  ```bash
  nc -l 12345
  ```

### `iptables`
- **Description**: Configure IPv4 firewall.
- **Explanation**: Manages rules; `-L` lists them.
- **Example**:
  ```bash
  sudo iptables -L
  ```

### `route`
- **Description**: Manage routing table.
- **Explanation**: Shows/modifies routes; `-n` for numeric.
- **Example**:
  ```bash
  route -n
  ```

### `ssh-keygen`
- **Description**: Generate SSH keys.
- **Explanation**: Creates key pairs for authentication.
- **Example**:
  ```bash
  ssh-keygen -t rsa -b 4096
  ```

### `nslookup`
- **Description**: Query DNS records.
- **Explanation**: Resolves hostnames to IPs.
- **Example**:
  ```bash
  nslookup google.com
  ```

### `dig`
- **Description**: Detailed DNS lookup.
- **Explanation**: Comprehensive DNS info; better than `nslookup`.
- **Example**:
  ```bash
  dig google.com
  ```

### `traceroute`
- **Description**: Trace network path.
- **Explanation**: Shows route to a host.
- **Example**:
  ```bash
  traceroute google.com
  ```

## IO Redirection

### `cmd < file`
- **Description**: Use file as input.
- **Explanation**: Redirects file contents to `cmd`.
- **Example**:
  ```bash
  wc -l < data.txt
  ```

### `cmd > file`
- **Description**: Redirect output to file.
- **Explanation**: Overwrites file with stdout.
- **Example**:
  ```bash
  ls > dirlist.txt
  ```

### `cmd 2> file`
- **Description**: Redirect errors to file.
- **Explanation**: Captures stderr.
- **Example**:
  ```bash
  ls /nonexistent 2> errors.log
  ```

### `cmd &> file`
- **Description**: Redirect all output to file.
- **Explanation**: Combines stdout and stderr.
- **Example**:
  ```bash
  make &> build.log
  ```

### `cmd >> file`
- **Description**: Append output to file.
- **Explanation**: Adds stdout without overwriting.
- **Example**:
  ```bash
  echo "Log entry" >> logfile.txt
  ```

### `tee`
- **Description**: Split output to file and stdout.
- **Explanation**: Writes to both; `-a` appends.
- **Example**:
  ```bash
  ls | tee output.txt
  ```

## Environment Variable Commands

### `export VARIABLE_NAME=value`
- **Description**: Set environment variable.
- **Explanation**: Makes variable available to shell/subprocesses.
- **Example**:
  ```bash
  export MY_VAR="Hello"
  ```

### `echo $VARIABLE_NAME`
- **Description**: Display variable value.
- **Explanation**: Prints the variable’s content.
- **Example**:
  ```bash
  echo $PATH
  ```

### `env`
- **Description**: List environment variables.
- **Explanation**: Shows all current variables.
- **Example**:
  ```bash
  env
  ```

### `unset VARIABLE_NAME`
- **Description**: Remove variable.
- **Explanation**: Deletes from environment.
- **Example**:
  ```bash
  unset MY_VAR
  ```

### `printenv`
- **Description**: Print variables.
- **Explanation**: Shows specific or all variables.
- **Example**:
  ```bash
  printenv PATH
  ```

## User Management Commands

### `who`
- **Description**: List logged-in users.
- **Explanation**: Shows active users and details.
- **Example**:
  ```bash
  who
  ```

### `sudo adduser username`
- **Description**: Add new user.
- **Explanation**: Prompts for user info (e.g., password).
- **Example**:
  ```bash
  sudo adduser newuser
  ```

### `finger`
- **Description**: Show user info.
- **Explanation**: Displays login time, etc. (if installed).
- **Example**:
  ```bash
  finger newuser
  ```

### `sudo deluser user groupname`
- **Description**: Remove user from group.
- **Explanation**: Removes group membership.
- **Example**:
  ```bash
  sudo deluser newuser sudo
  ```

### `last`
- **Description**: Show login history.
- **Explanation**: Lists past logins from `/var/log/wtmp`.
- **Example**:
  ```bash
  last
  ```

### `sudo userdel -r username`
- **Description**: Delete user and files.
- **Explanation**: Removes user and home dir (`-r`).
- **Example**:
  ```bash
  sudo userdel -r olduser
  ```

### `sudo passwd -l username`
- **Description**: Lock user account.
- **Explanation**: Disables login by locking password.
- **Example**:
  ```bash
  sudo passwd -l newuser
  ```

### `su - username`
- **Description**: Switch user.
- **Explanation**: Starts shell as user; `-` loads environment.
- **Example**:
  ```bash
  su - newuser
  ```

### `sudo usermod -a -G groupname username`
- **Description**: Add user to group.
- **Explanation**: Appends (`-a`) to group (`-G`).
- **Example**:
  ```bash
  sudo usermod -a -G developers newuser
  ```

### `id`
- **Description**: Show user/group IDs.
- **Explanation**: Lists UID, GID, and groups.
- **Example**:
  ```bash
  id newuser
  ```

## Shell Commands

### `alias`
- **Description**: Create command shortcuts.
- **Explanation**: Defines aliases; persist in `.bashrc`.
- **Example**:
  ```bash
  alias ll="ls -l"
  ```

### `source`
- **Description**: Run script in current shell.
- **Explanation**: Executes in current env (alias: `.`).
- **Example**:
  ```bash
  source ~/.bashrc
  ```

### `history`
- **Description**: Show command history.
- **Explanation**: Lists past commands.
- **Example**:
  ```bash
  history
  ```

### `type`
- **Description**: Identify command type.
- **Explanation**: Shows if alias, function, or binary.
- **Example**:
  ```bash
  type ls
  ```

## Scheduling Commands

### `crontab`
- **Description**: Schedule recurring tasks.
- **Explanation**: Manages cron jobs; `-e` edits, `-l` lists.
- **Example**:
  ```bash
  crontab -e
  ```
  Add: `0 1 * * * backup.sh` (1 AM daily).

### `at`
- **Description**: Schedule one-time task.
- **Explanation**: Runs command at specified time.
- **Example**:
  ```bash
  echo "backup.sh" | at now + 1 hour
  ```

## Text Processing Commands

### `grep`
- **Description**: Search text for patterns.
- **Explanation**: Finds matching lines; `-r` for recursive.
- **Example**:
  ```bash
  grep -r "error" /var/log
  ```

### `awk`
- **Description**: Process text data.
- **Explanation**: Extracts/manipulates by fields/patterns.
- **Example**:
  ```bash
  awk '{print $1}' access.log
  ```

### `sed`
- **Description**: Edit text streams.
- **Explanation**: Substitutes with `s/pattern/replace/`.
- **Example**:
  ```bash
  sed 's/foo/bar/g' file.txt
  ```

### `diff`
- **Description**: Compare files.
- **Explanation**: Shows line-by-line differences.
- **Example**:
  ```bash
  diff file1.txt file2.txt
  ```

### `sort`
- **Description**: Sort text lines.
- **Explanation**: Orders alphabetically or numerically (`-n`).
- **Example**:
  ```bash
  sort -n numbers.txt
  ```

### `cut`
- **Description**: Extract text sections.
- **Explanation**: Cuts by delimiter (`-d`) and field (`-f`).
- **Example**:
  ```bash
  cut -d',' -f2 data.csv
  ```

### `wc`
- **Description**: Count lines/words/chars.
- **Explanation**: Uses `-l` (lines), `-w` (words), `-c` (chars).
- **Example**:
  ```bash
  wc -l script.sh
  ```

### `uniq`
- **Description**: Remove duplicate lines.
- **Explanation**: Filters adjacent duplicates; pair with `sort`.
- **Example**:
  ```bash
  sort file.txt | uniq
  ```

### `tr`
- **Description**: Translate characters.
- **Explanation**: Replaces or deletes characters.
- **Example**:
  ```bash
  echo "HELLO" | tr 'A-Z' 'a-z'
  ```

## General Commands

### `man`
- **Description**: Show command manuals.
- **Explanation**: Provides detailed docs.
- **Example**:
  ```bash
  man grep
  ```

### `which`
- **Description**: Locate executable.
- **Explanation**: Shows command path.
- **Example**:
  ```bash
  which bash
  ```

### `sudo`
- **Description**: Run as superuser.
- **Explanation**: Grants elevated privileges.
- **Example**:
  ```bash
  sudo apt update
  ```

### `whatis`
- **Description**: Brief command description.
- **Explanation**: One-line summary from man pages.
- **Example**:
  ```bash
  whatis ls
  ```

### `whereis`
- **Description**: Find binary/source/man pages.
- **Explanation**: Locates all related files.
- **Example**:
  ```bash
  whereis bash
  ```

## System Control Commands

### `shutdown`
- **Description**: Shut down or reboot.
- **Explanation**: `-h` (halt), `-r` (reboot), time arg.
- **Example**:
  ```bash
  sudo shutdown -r now
  ```

### `reboot`
- **Description**: Restart system.
- **Explanation**: Immediate reboot.
- **Example**:
  ```bash
  sudo reboot
  ```

### `halt`
- **Description**: Stop system.
- **Explanation**: Halts processes; use cautiously.
- **Example**:
  ```bash
  sudo halt
  ```

### `poweroff`
- **Description**: Power off system.
- **Explanation**: Shuts down cleanly.
- **Example**:
  ```bash
  sudo poweroff
  ```

## Bash Shortcuts

- **Ctrl + A**: Start of line.
- **Ctrl + E**: End of line.
- **Ctrl + B**: Back one char.
- **Ctrl + F**: Forward one char.
- **Alt + B**: Back one word.
- **Alt + F**: Forward one word.
- **Ctrl + U**: Cut to line start.
- **Ctrl + K**: Cut to line end.
- **Ctrl + W**: Cut previous word.
- **Ctrl + Y**: Paste cut text.
- **Ctrl + L**: Clear screen.
- **Ctrl + R**: Search history.
- **Ctrl + G**: Exit history search.
- **Ctrl + P**: Previous command.
- **Ctrl + N**: Next command.
- **Ctrl + C**: Kill command.

## Nano Shortcuts

- **Ctrl + O**: Save file.
- **Ctrl + X**: Exit.
- **Ctrl + R**: Read file.
- **Ctrl + J**: Justify paragraph.
- **Ctrl + Y**: Scroll up.
- **Ctrl + V**: Scroll down.
- **Alt + \\**: Go to line.
- **Alt + ,**: Line start.
- **Alt + .**: Line end.
- **Ctrl + K**: Cut to end.
- **Ctrl + U**: Paste.
- **Ctrl + 6**: Select text.
- **Ctrl + W**: Search.
- **Alt + W**: Replace.
- **Alt + R**: Repeat search.

## VI Shortcuts

- **cw**: Change word.
- **dd**: Delete line.
- **x**: Delete char.
- **R**: Replace mode.
- **o**: New line below.
- **u**: Undo.
- **s**: Substitute char.
- **dw**: Delete word.
- **D**: Delete to end.
- **4dw**: Delete 4 words.
- **A**: Append at end.
- **S**: Delete and insert.
- **r**: Replace char.
- **i**: Insert before.
- **3dd**: Delete 3 lines.
- **ESC**: Command mode.
- **U**: Undo line.
- **~**: Toggle case.
- **a**: Append after.
- **C**: Change to end.

## Vim Shortcuts

- **i**: Insert mode.
- **x**: Delete char.
- **dd**: Delete line.
- **yy**: Copy line.
- **p**: Paste below.
- **u**: Undo.
- **Ctrl + R**: Redo.
- **:w**: Save.
- **:q**: Quit.
- **:wq**: Save and quit.
- **:q!**: Quit no save.
- **:set nu**: Line numbers.
- **v**: Visual mode.
- **y**: Copy selection.
- **d**: Delete selection.
- **p**: Paste selection.
- **:s/old/new/g**: Replace in line.

## Package Management Commands

### `apt update`
- **Description**: Update package list (Debian/Ubuntu).
- **Explanation**: Refreshes package index.
- **Example**:
  ```bash
  sudo apt update
  ```

### `apt upgrade`
- **Description**: Upgrade packages.
- **Explanation**: Updates all installed packages.
- **Example**:
  ```bash
  sudo apt upgrade
  ```

### `apt install package_name`
- **Description**: Install package.
- **Explanation**: Adds package and dependencies.
- **Example**:
  ```bash
  sudo apt install nginx
  ```

### `apt remove package_name`
- **Description**: Remove package.
- **Explanation**: Uninstalls, keeps config files.
- **Example**:
  ```bash
  sudo apt remove nginx
  ```

### `apt search pattern`
- **Description**: Search packages.
- **Explanation**: Finds packages by keyword.
- **Example**:
  ```bash
  apt search python
  ```

### `apt list --installed`
- **Description**: List installed packages.
- **Explanation**: Shows current packages.
- **Example**:
  ```bash
  apt list --installed
  ```

### `dpkg -i package.deb`
- **Description**: Install `.deb` file.
- **Explanation**: Manual install of local package.
- **Example**:
  ```bash
  sudo dpkg -i package.deb
  ```

### `yum update`
- **Description**: Update packages (RPM).
- **Explanation**: Updates all (e.g., CentOS).
- **Example**:
  ```bash
  sudo yum update
  ```

### `yum install package_name`
- **Description**: Install package (RPM).
- **Explanation**: Adds package and dependencies.
- **Example**:
  ```bash
  sudo yum install httpd
  ```

### `dnf search term`
- **Description**: Search packages (Fedora).
- **Explanation**: Modern RPM search.
- **Example**:
  ```bash
  dnf search vim
  ```

### `pacman -S package_name`
- **Description**: Install package (Arch).
- **Explanation**: Adds package and dependencies.
- **Example**:
  ```bash
  sudo pacman -S vim
  ```

### `pacman -Syu`
- **Description**: Update system (Arch).
- **Explanation**: Syncs and updates all.
- **Example**:
  ```bash
  sudo pacman -Syu
  ```

### `zypper install package_name`
- **Description**: Install package (openSUSE).
- **Explanation**: Adds package and dependencies.
- **Example**:
  ```bash
  sudo zypper install vim
  ```

## Disk Space Usage & Monitoring

### `df -h`
- **Description**: Show disk usage.
- **Explanation**: Displays space in human-readable format.
- **Example**:
  ```bash
  df -h
  ```

### `du -sh /path`
- **Description**: Show directory size.
- **Explanation**: Summarizes size (`-s`), readable (`-h`).
- **Example**:
  ```bash
  du -sh /var/log
  ```

### `du -h --max-depth=1`
- **Description**: List subdir sizes.
- **Explanation**: Shows sizes one level deep.
- **Example**:
  ```bash
  du -h --max-depth=1 /home
  ```

### `lsblk`
- **Description**: List block devices.
- **Explanation**: Shows partitions and mounts.
- **Example**:
  ```bash
  lsblk
  ```

### `blkid`
- **Description**: Show partition UUIDs.
- **Explanation**: Identifies filesystem details.
- **Example**:
  ```bash
  sudo blkid
  ```

### `findmnt`
- **Description**: List mounted filesystems.
- **Explanation**: Shows mount points and properties.
- **Example**:
  ```bash
  findmnt
  ```

### `mount | column -t`
- **Description**: List mounts in table.
- **Explanation**: Formats `mount` output cleanly.
- **Example**:
  ```bash
  mount | column -t
  ```

## Partition & Filesystem Management

### `fdisk -l`
- **Description**: List partitions.
- **Explanation**: Shows all disk partitions (root).
- **Example**:
  ```bash
  sudo fdisk -l
  ```

### `parted -l`
- **Description**: Show partition details.
- **Explanation**: Displays layout via GNU Parted.
- **Example**:
  ```bash
  sudo parted -l
  ```

### `mkfs.ext4 /dev/sdb1`
- **Description**: Format as ext4.
- **Explanation**: Creates ext4; erases data.
- **Example**:
  ```bash
  sudo mkfs.ext4 /dev/sdb1
  ```

### `mkfs.xfs /dev/sdb1`
- **Description**: Format as XFS.
- **Explanation**: Creates XFS; erases data.
- **Example**:
  ```bash
  sudo mkfs.xfs /dev/sdb1
  ```

### `e2fsck -f /dev/sdb1`
- **Description**: Check/repair ext4.
- **Explanation**: Forces check (`-f`) for errors.
- **Example**:
  ```bash
  sudo e2fsck -f /dev/sdb1
  ```

### `xfs_repair /dev/sdb1`
- **Description**: Repair XFS.
- **Explanation**: Fixes XFS issues.
- **Example**:
  ```bash
  sudo xfs_repair /dev/sdb1
  ```

### `tune2fs -m 5 /dev/sdb1`
- **Description**: Set ext4 reserved space.
- **Explanation**: Reserves 5% for root.
- **Example**:
  ```bash
  sudo tune2fs -m 5 /dev/sdb1
  ```

## Mounting & Unmounting Filesystems

### `mount /dev/sdb1 /mnt`
- **Description**: Mount partition.
- **Explanation**: Attaches filesystem to dir.
- **Example**:
  ```bash
  sudo mount /dev/sdb1 /mnt
  ```

### `umount /mnt`
- **Description**: Unmount filesystem.
- **Explanation**: Detaches from mount point.
- **Example**:
  ```bash
  sudo umount /mnt
  ```

### `mount -o remount,rw /`
- **Description**: Remount with options.
- **Explanation**: Changes options (e.g., read-write).
- **Example**:
  ```bash
  sudo mount -o remount,rw /
  ```

### `mount -t nfs server:/share /mnt`
- **Description**: Mount NFS share.
- **Explanation**: Connects to remote NFS.
- **Example**:
  ```bash
  sudo mount -t nfs 192.168.1.100:/share /mnt
  ```

### `mount -o loop file.iso /mnt`
- **Description**: Mount ISO file.
- **Explanation**: Treats ISO as device.
- **Example**:
  ```bash
  sudo mount -o loop disk.iso /mnt
  ```

## Disk Performance & Health Monitoring

### `iotop`
- **Description**: Monitor disk I/O.
- **Explanation**: Shows real-time I/O per process.
- **Example**:
  ```bash
  sudo iotop
  ```

### `iostat -x 1`
- **Description**: Show disk stats.
- **Explanation**: Reports I/O every second.
- **Example**:
  ```bash
  iostat -x 1
  ```

### `smartctl -H /dev/sda`
- **Description**: Check disk health.
- **Explanation**: Verifies SMART status.
- **Example**:
  ```bash
  sudo smartctl -H /dev/sda
  ```

### `smartctl -a /dev/sda`
- **Description**: Show SMART data.
- **Explanation**: Full SMART attributes.
- **Example**:
  ```bash
  sudo smartctl -a /dev/sda
  ```

### `badblocks -sv /dev/sdb`
- **Description**: Scan for bad sectors.
- **Explanation**: Verbose scan with output.
- **Example**:
  ```bash
  sudo badblocks -sv /dev/sdb
  ```

## Managing Disk Quotas

### `quota -u username`
- **Description**: Show user quota.
- **Explanation**: Displays usage/limits.
- **Example**:
  ```bash
  quota -u user1
  ```

### `edquota -u username`
- **Description**: Edit user quota.
- **Explanation**: Opens editor for quota settings.
- **Example**:
  ```bash
  sudo edquota -u user1
  ```

### `repquota -a`
- **Description**: Report all quotas.
- **Explanation**: Summarizes system-wide usage.
- **Example**:
  ```bash
  sudo repquota -a
  ```

### `setquota -u username 500M 1G 0 0 /dev/sda1`
- **Description**: Set user quota.
- **Explanation**: Soft (500MB), hard (1GB) limits.
- **Example**:
  ```bash
  sudo setquota -u user1 500M 1G 0 0 /dev/sda1
  ```

## LVM (Logical Volume Management)

### `pvcreate /dev/sdb`
- **Description**: Initialize physical volume.
- **Explanation**: Prepares disk for LVM.
- **Example**:
  ```bash
  sudo pvcreate /dev/sdb
  ```

### `vgcreate vg_name /dev/sdb`
- **Description**: Create volume group.
- **Explanation**: Groups physical volumes.
- **Example**:
  ```bash
  sudo vgcreate my_vg /dev/sdb
  ```

### `lvcreate -L 10G -n lv_name vg_name`
- **Description**: Create logical volume.
- **Explanation**: Allocates 10GB from group.
- **Example**:
  ```bash
  sudo lvcreate -L 10G -n my_lv my_vg
  ```

### `lvextend -L +5G /dev/vg_name/lv_name`
- **Description**: Extend logical volume.
- **Explanation**: Adds 5GB to LV.
- **Example**:
  ```bash
  sudo lvextend -L +5G /dev/my_vg/my_lv
  ```

### `resize2fs /dev/vg_name/lv_name`
- **Description**: Resize ext4 on LV.
- **Explanation**: Adjusts filesystem size.
- **Example**:
  ```bash
  sudo resize2fs /dev/my_vg/my_lv
  ```

## Swap Space Management

### `swapon -s`
- **Description**: Show swap areas.
- **Explanation**: Lists active swap and usage.
- **Example**:
  ```bash
  swapon -s
  ```

### `free -m`
- **Description**: Show memory/swap.
- **Explanation**: Displays in megabytes.
- **Example**:
  ```bash
  free -m
  ```

### `mkswap /dev/sdb2`
- **Description**: Format swap partition.
- **Explanation**: Prepares partition for swap.
- **Example**:
  ```bash
  sudo mkswap /dev/sdb2
  ```

### `swapon /dev/sdb2`
- **Description**: Enable swap partition.
- **Explanation**: Activates swap area.
- **Example**:
  ```bash
  sudo swapon /dev/sdb2
  ```

### `swapoff /dev/sdb2`
- **Description**: Disable swap partition.
- **Explanation**: Deactivates swap area.
- **Example**:
  ```bash
  sudo swapoff /dev/sdb2
  ```

### `fallocate -l 2G /swapfile`
- **Description**: Create swap file.
- **Explanation**: Allocates 2GB for swap.
- **Example**:
  ```bash
  sudo fallocate -l 2G /swapfile
  ```

### `mkswap /swapfile`
- **Description**: Format swap file.
- **Explanation**: Sets up file as swap.
- **Example**:
  ```bash
  sudo mkswap /swapfile
  ```

### `swapon /swapfile`
- **Description**: Enable swap file.
- **Explanation**: Activates file-based swap.
- **Example**:
  ```bash
  sudo swapon /swapfile
  ```

## Secure Disk Erasing

### `shred -n 3 -z /dev/sdb`
- **Description**: Securely erase disk.
- **Explanation**: Overwrites 3 times, then zeros.
- **Example**:
  ```bash
  sudo shred -n 3 -z /dev/sdb
  ```

### `dd if=/dev/zero of=/dev/sdb bs=1M status=progress`
- **Description**: Wipe with zeros.
- **Explanation**: Fills disk with zeros, shows progress.
- **Example**:
  ```bash
  sudo dd if=/dev/zero of=/dev/sdb bs=1M status=progress
  ```

### `wipe -rf /dev/sdb`
- **Description**: Secure wipe (needs `wipe`).
- **Explanation**: Erases recursively and forcefully.
- **Example**:
  ```bash
  sudo wipe -rf /dev/sdb
  ```
