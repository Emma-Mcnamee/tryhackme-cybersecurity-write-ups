# Linux Fundamentals Part 2 — Lab 1: Remote Login — TryHackMe
**Difficulty:** Easy  
**Time:** ~20 minutes  
**Goal:** Practice logging into a remote Linux machine using SSH.

---

## Summary
In this lab, I practiced connecting to a remote Linux machine via SSH. The objective was to log in as a standard user from an attack box, demonstrating understanding of remote access and basic SSH commands.

---

## Tools Used
- TryHackMe Attack Box terminal  
- Linux commands: `ssh`  

---

## Steps / Playbook

1. **Launch Attack Box**
   - Opened the TryHackMe Linux attack box.  
   - Verified current user and IP:  
     ```
     root@10.201.6.59
     ```

2. **Connecting to target machine**
   - Used SSH to log in to the remote machine with credentials provided:  
     ```
     ssh tryhackme@10.201.82.27
     ```  
   - Entered password: `tryhackme`.  

3. **Successful login**
   - After entering credentials, terminal confirmed login as user `tryhackme` on the remote machine.  
   - Verified current user and location:  
     ```
     whoami
     pwd
     ```
   - Confirmed active session as `tryhackme` inside the target Linux machine.  

---

## Results
- Successfully logged in remotely via SSH.  
- Gained a remote shell session as `tryhackme` user.  

---

## Lessons Learned
- `ssh user@ip_address` is the standard way to remotely connect to a Linux system.  
- Password authentication allows login if key-based authentication is not set up.  
- Verifying the current user (`whoami`) ensures correct permissions on the target system.  

---

## References
- [SSH Command Basics](https://linuxize.com/post/how-to-use-ssh-to-connect-to-a-remote-server-in-linux/)
