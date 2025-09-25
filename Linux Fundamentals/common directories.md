# Linux Fundamentals Part 2 — Exploring Common Directories — TryHackMe
**Difficulty:** Easy  
**Time:** ~20 minutes  
**Goal:** Explore common Linux directories (`/etc`, `/var`, `/home/root`, `/tmp`) and understand their purpose.

---

## Summary
In this lab, I explored common Linux directories to understand where different types of files are stored. The exercise focused on `/var` and `/var/log` while highlighting potential pitfalls when navigating as different users.

---

## Tools Used
- TryHackMe remote Linux machine (`user2@linux2`)  
- Linux commands: `cd`, `ls`, `grep`  

---

## Steps / Playbook

1. **Navigate to `/var`**
   - Switched to the `/var` directory:  
     ```
     cd /var
     ls
     ```  
   - Observed multiple directories and chose to explore `log`.

2. **Explore `/var/log`**
   - Entered the directory:  
     ```
     cd log
     ls
     ```  
   - Found numerous subdirectories and log files.  

3. **Search for specific file types**
   - Attempted to find `.txt` files using:  
     ```
     grep .txt
     ```  
   - Output returned nothing.  

4. **Encountered navigation issue**
   - Noticed that the machine was no longer working properly from `user2@linux2`.  
   - Could not easily return to the home directory.  
   - Made a note to research proper navigation and environment management in future lessons.

---

## Results
- Successfully explored `/var` and `/var/log` directories.  
- Understood that log files are stored in `/var/log`.  
- Experienced a navigation issue that highlighted the importance of knowing your current environment and user context.

---

## Lessons Learned
- `/var` stores variable data, including logs and frequently updated files.  
- `/var/log` contains system and application log files.  
- Always verify which user you are logged in as before performing tasks.  
- Navigation commands (`cd ~` or `cd /home/username`) are helpful for returning to a known location.  

---

## References
- [Linux Directory Structure Overview](https://www.tecmint.com/linux-directory-structure-explained/)
- [Understanding /var and /var/log](https://www.tecmint.com/understand-linux-directory-structure/)
