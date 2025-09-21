# Linux Fundamentals Part 2 — Switch Users & View Important File — TryHackMe
**Difficulty:** Easy  
**Time:** ~20 minutes  
**Goal:** Switch users in Linux and access a file owned by another user.

---

## Summary
In this lab, I practiced identifying file ownership, switching users with `su`, and viewing contents of a file owned by a different user. The exercise reinforced Linux permissions and the importance of using `su` with the proper arguments to fully assume another user’s environment.

---

## Tools Used
- TryHackMe remote Linux machine (`tryhackme@linux2`)  
- Linux commands: `ls -l`, `su`, `cat`  

---

## Steps / Playbook

1. **Check file ownership**
   - Listed file permissions to determine the owner of `important`:  
     ```
     ls -l
     ```  
   - Output showed `user2` as the sole owner of the file `important`.

2. **Switch users**
   - Attempted to switch to `user2` using:  
     ```
     su
     ```  
   - Entered password: `user2`  
   - Realized I did not use the `-l` flag, so the environment remained in `tryhackme`’s home directory.

3. **Proper user switch**
   - Used the correct command to fully switch to `user2`’s environment:  
     ```
     su -l user2
     ```  
   - Confirmed the session environment reflected `user2`.

4. **View file contents**
   - Displayed the contents of the file `important`:  
     ```
     cat important
     ```  
   - Output: `THM{SU_USER2}`  

---

## Results
- Successfully switched users to `user2` using `su -l`.  
- Accessed the contents of `important` file: `THM{SU_USER2}`.  

---

## Lessons Learned
- `ls -l` shows file permissions and ownership.  
- `su username` switches users but may not load their full environment.  
- `su -l username` ensures a login shell with the target user’s environment.  
- Always verify you are in the correct user environment before performing tasks.  

---

## References
- [Linux su Command Guide](https://linuxize.com/post/su-command-in-linux/)
