# Linux Fundamentals Part 2 — Filesystem Continued — TryHackMe
**Difficulty:** Easy  
**Time:** ~30 minutes  
**Goal:** Practice creating, moving, and inspecting files using basic Linux filesystem commands.

---

## Summary
In this lab, I practiced Linux filesystem commands including `touch`, `mkdir`, `cp`, `mv`, `rm`, `file`, and `su`. The tasks included creating a new file, checking file types, moving files between directories, and reading file contents.

---

## Tools Used
- TryHackMe remote Linux machine (`tryhackme@linux2`)  
- Linux commands: `touch`, `mkdir`, `mv`, `ls`, `cd`, `file`, `cat`  

---

## Steps / Playbook

1. **Creating a new file**
   - Logged in remotely as `tryhackme@linux2`.  
   - Created a new file called `newnote`:  
     ```
     touch newnote
     ```  
   - Verified creation with:  
     ```
     ls
     ```  
   - Files listed: `important`, `myfile`, `myfolder`, `newnote`, `unknown1`.

2. **Checking file type**
   - Determined the type of `unknown1` file:  
     ```
     file unknown1
     ```  
   - Output: `ASCII text`.

3. **Moving a file**
   - Returned to home directory:  
     ```
     cd /home/tryhackme
     ```  
   - Moved `myfile` into folder `myfolder`:  
     ```
     mv myfile myfolder
     ```  
   - Verified move by navigating to folder and listing contents:  
     ```
     cd myfolder
     ls
     ```  

4. **Viewing file contents**
   - Displayed the contents of `myfile` to complete the task:  
     ```
     cat myfile
     ```  
   - Output: `THM{FILESYSTEM}`

---

## Results
- Successfully created a new file `newnote`.  
- Identified `unknown1` as an ASCII text file.  
- Moved `myfile` into `myfolder` successfully.  
- Verified file contents with `cat` command.

---

## Lessons Learned
- `touch filename` creates an empty file.  
- `file filename` identifies the type of a file.  
- `mv source destination` moves files or directories.  
- Always verify operations by using `ls` or `cat`.  

---

## References
- [Linux File Management Commands](https://linuxize.com/post/linux-file-management-commands/)
