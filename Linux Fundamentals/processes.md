# Processes — TryHackMe
**Difficulty:** Easy  
**Time:** ~20–25 minutes  
**Goal:** Learn how to locate running processes on a Linux instance and find a hidden flag.

---

## Summary
In this lab, I practiced identifying processes running on a deployed Linux instance. The task was to locate a process that contained a hidden flag. I used Linux commands to list processes and troubleshoot how to view the full process name/PID.

---

## Tools Used
- TryHackMe Attack Box and deployed Linux VM  
- Commands: `ps aux`, `tr`, Linux process navigation commands  
- External resources: online searches for Linux process commands

---

## Steps / Playbook

1. **Reconnect to deployed instance**
   - Used the terminal connected to the deployed Linux instance.  
   - Ensured I was logged in as `tryhackme` on the correct IP.

2. **List running processes**
   - Used the command:
     ```bash
     ps aux
     ```
   - Output listed all processes from all users.  

3. **Scan for unusual processes**
   - Looked for out-of-the-ordinary PIDs or process names.  
   - Found a process listed as `THM{PR`, which resembled the start of the flag.  

4. **Troubleshoot incomplete flag**
   - The lab indicated the flag is 15 characters, but the output only showed part of it.  
   - Tried navigating to the process with `cd` — received “not a directory” error.  
   - Realized a process cannot be accessed like a file system directory.  

5. **Research ways to view full PID**
   - Found that PIDs are often truncated in `ps` output.  
   - Learned multiple ways to reveal the full process name.  
   - The most direct option is to read the command line exactly as the kernel sees it:  
     ```
     /proc/<pid>/cmdline
     ```
   - Noted that the output shows the line without spaces, which is hard to read.  
   - Learned that using `tr` can add spaces to make it readable.  

6. **Reveal the full flag**
   - Entered the command:
     ```bash
     tr < /proc/<THM{PR>/cmdline
     ```
   - This revealed the full process ID and the flag:  
     ```
     THM{PROCESSES}
     ```

---

## Results
- Successfully located the process containing the hidden flag.  
- Learned that truncated process names in `ps aux` can be read fully via `/proc/<pid>/cmdline`.  
- Flag obtained: `THM{PROCESSES}`.

---

## Lessons Learned
- `ps aux` is useful for listing all processes, but long process names may be truncated.  
- `/proc/<pid>/cmdline` shows the full command line as the kernel sees it.  
- Using `tr` helps format the output with spaces for readability.  
- Process IDs and names are not directories — attempting to navigate them with `cd` fails.  
- Online research is valuable for troubleshooting Linux commands.  

---

## Tip
- Try `ps aux | grep THM` to quickly locate processes containing the flag.  
- Use `ps auxww` to see full process names if truncated in standard output.
