# Linux Fundamentals: Using `grep` to find flags in a log file

## Overview
This lab focused on using `grep` to search through log files for a specific pattern. The objective was to locate a flag in `access.log` that begins with the prefix `THM`. Being able to quickly search large text files with `grep` is a fundamental skill for log analysis and many defensive/offensive Linux tasks.

## Steps Taken
1. I opened my Linux VM from the previous lab and located the `access.log` file.  
2. I ran a simple `grep` search for the `THM` prefix to find the flag inside the log:  
   ```bash
   grep "THM" access.log
The command returned a line (a string of text) from the log that contained the flag.

I examined the returned text and identified the flag within that output (the flag had the prefix THM).

## Commands Used

grep "THM" access.log — search the access.log file for any occurrence of the string THM.

## Key Takeaways

grep is an efficient way to locate specific strings or patterns inside large text files.

Searching for a unique prefix (like THM) helps narrow results quickly when you don’t know the full flag.

Always inspect the full line returned by grep — flags are often embedded in surrounding text.
