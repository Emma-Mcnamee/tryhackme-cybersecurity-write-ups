
# Linux Fundamentals Part 1, lab 1 — TryHackMe
**Difficulty:** Easy  
**Time:** ~30 minutes  
**Goal:** Navigate the Linux filesystem, list directories/files, and read file contents.

---

## Summary
This room guided me through basic Linux filesystem navigation. The objective was to locate a file within nested directories and read its contents using basic commands. I practiced using `ls`, `cd`, and `cat` while learning the importance of specifying the correct path.

---

## Tools Used
- TryHackMe web terminal
- Linux commands: `ls`, `cd`, `cat`

---

## Steps / Playbook

1. **Initial exploration**
   - Logged in as `tryhackme@linux1`.
   - Used `ls` to list directories in the home folder: `folder1`, `folder2`, `folder3`, `folder4`.

2. **Navigating directories**
   - Attempted `/home/tryhackme` without `cd` → system returned "directory type" error.
   - Tried `cd folder2` while still in `folder1` → system returned "no such file in directory."
   - Learned to always use `cd` to change directories first.

3. **Systematic search**
   - Returned home: `cd /home/tryhackme`.
   - Checked `folder1` → empty (`ls` returned no files).
   - Checked `folder2` → empty.
   - Checked `folder3` → empty.
   - Checked `folder4` → found file `note.txt`.

4. **Reading file contents**
   - Used `cat note.txt` → output: `Hello World!`

---

## Results
- Located file: `note.txt`  
- Contents: `Hello World!`  

---

## Lessons Learned
- Always use `cd` to move into directories; typing a path without it doesn’t change your location.  
- `ls` is essential for checking directory contents.  
- Systematic navigation prevents getting lost in nested folders.  
- Using `cat` is the simplest way to read file contents in Linux.  

---

## References
- [Linux Command Basics Cheat Sheet](https://linuxcommand.org/lc3_learning_the_shell.php)
