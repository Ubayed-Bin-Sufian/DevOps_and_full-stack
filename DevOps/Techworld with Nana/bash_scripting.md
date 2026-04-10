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

## References:

1. [Bash Scripting Tutorial for Beginners](https://www.youtube.com/watch?v=PNhq_4d-5ek&t=368s)
2. Download the sample log file from the handout as mentioned in the video.