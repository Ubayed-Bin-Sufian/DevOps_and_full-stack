# Bash Scripting

## What is Bash Scripting and Why Use It?

Bash scripting is a powerful way to automate tasks in Unix-like operating systems. It allows you to write a series of commands in a file, which can then be executed as a script. This can save time and reduce the chance of errors when performing repetitive tasks.

## 1. Example of manual log analysis

1. `cd logs`
2. `cat application.log`
3. `grep "ERROR" application.log`
4. `grep -c "ERROR" application.log`: counts the number of lines containing "ERROR"
5. `grep "FATAL" application.log`
6. `grep -c "FATAL" application.log`
7. `grep "ERROR" system.log`
8. `grep -c "ERROR" system.log`
9. `grep "FATAL" system.log`
10. `grep -c "FATAL" system.log`
11. `find . -name "*.log" -mtime -1`: finds log files modified in the last 24 hours
    - `mtime`: modification time in days
    - `-1`: modified within the last 24 hours

## 2. Creating a Bash Script for Log Analysis

1. Create a new file: `touch log_analysis.sh`
2. `vim log_analysis.sh`: open the file in a text editor
3. Press `i` to enter insert mode in Vim
4. Add the following content to the file:  

```bash
#!/bin/bash

# Log Analysis Script

echo "Analyzing log files..."

# Count ERROR messages in application.log
error_count=$(grep -c "ERROR" application.log)
echo "Number of ERROR messages in application.log: $error_count"

# Count FATAL messages in application.log
fatal_count=$(grep -c "FATAL" application.log)
echo "Number of FATAL messages in application.log: $fatal_count"

# Count ERROR messages in system.log
error_count_system=$(grep -c "ERROR" system.log)
echo "Number of ERROR messages in system.log: $error_count_system"

# Count FATAL messages in system.log
fatal_count_system=$(grep -c "FATAL" system.log)
echo "Number of FATAL messages in system.log: $fatal_count_system"
```

5. Press `Esc` to exit insert mode, then type `:wq` to save and quit Vim
6. Make the script executable: `chmod +x log_analysis.sh`
7. Run the script: `./log_analysis.sh`

## References:

1. [Bash Scripting Tutorial for Beginners](https://www.youtube.com/watch?v=PNhq_4d-5ek&t=368s)
2. Download the sample log file from the handout as mentioned in the video.