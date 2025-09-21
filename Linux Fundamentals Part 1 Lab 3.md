# Intro to Shell Operators — TryHackMe
**Difficulty:** Easy  
**Time:** ~30 minutes  
**Goal:** Practice using shell operators (`&`, `&&`, `>`, `>>`) to manipulate file contents safely.

---

## Summary
In this lab, I learned how to use basic shell operators to control command execution and add data to files. I practiced using `>` and `>>` to redirect output to a file without losing existing data. The exercise reinforced the importance of verifying file contents before modifying them.

---

## Tools Used
- TryHackMe web terminal  
- Linux commands: `ls`, `cd`, `cat`, `echo`  
- Shell operators: `>`, `>>`

---

## Steps / Playbook

1. **Directory exploration**
   - Used `ls` to view available directories: `folder1`, `folder2`, `folder3`, `folder4`.  
   - Recalled from a previous lab that `folder4` contains a file, so navigated there:  
     ```
     cd folder4
     ls
     ```  
   - Found the file: `note.txt`.  

2. **Returning home**
   - To prepare for testing shell operators, returned to home directory:  
     ```
     cd /home/tryhackme
     ```  
   - Noted the file name `note.txt` for later use.  

3. **Adding text to a file without overwriting**
   - To append text without erasing existing content, used the `>>` operator:  
     ```
     echo "rock and roll" >> note.txt
     ```  
   - Verified the contents of the file:  
     ```
     cat note.txt
     ```  
   - Observed that `rock and roll` was added successfully. Noted that the previous content may have been empty or overwritten in earlier attempts.  

4. **Lesson learned**
   - Always check a file’s contents before appending or overwriting.  
   - `>` overwrites a file completely; `>>` appends text to the end.  
   - Using operators safely ensures you do not accidentally delete important data.  

---

## Results
- Successfully appended text to `note.txt` using `>>`.  
- Verified contents using `cat`.  

---

## Lessons Learned
- `>>` appends to a file; `>` overwrites it.  
- Always verify file contents with `cat` before adding new data.  
- Basic shell operators can control file content safely when used correctly.  

---

## References
- [Linux Shell Operators Guide](https://linuxize.com/post/bash-redirection/)
