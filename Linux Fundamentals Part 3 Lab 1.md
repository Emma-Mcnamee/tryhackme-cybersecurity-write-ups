
# Terminal Text Editors — TryHackMe
**Difficulty:** Easy  
**Time:** ~15–25 minutes  
**Goal:** Learn basic terminal text editors (nano, vim) and locate a flag inside a provided file.

---

## Summary
In this lab I practiced using terminal text editors on a remote TryHackMe machine. I connected from the Attack Box via SSH, opened files with `nano`, and located the lab flag inside the `task3` file.

---

## Tools Used
- TryHackMe Attack Box and target Linux VM  
- Terminal editors: `nano`, `vim` (introductory)  
- Commands: `ssh`, `nano`, navigation keys, `Ctrl+X`

---

## Steps / Playbook

1. **Launch and connect**
   - Launched the TryHackMe Attack Box and started the target Linux VM.  
   - Connected from the attack box to the target machine:
     ```bash
     ssh tryhackme@10.201.55.58
     ```
     - Entered the provided password when prompted.

2. **Editor introduction**
   - The lab introduced two editors: `nano` (beginner-friendly) and `vim` (advanced).  
   - Started with `nano` to get comfortable with basic editing and menu commands.

3. **Create and inspect a file with `nano`**
   - Created/opened a new file with:
     ```bash
     nano <filename>
     ```
   - Read the command menu shown at the bottom of the `nano` editor to learn common shortcuts.  
   - Used `Ctrl + X` to exit the editor and return to the shell.

4. **Open `task3` and find flag**
   - Opened the provided file:
     ```bash
     nano task3
     ```
   - Located the lab flag inside the file:  
     ```
     THM{TEXT_EDITORS}
     ```

---

## Results
- Successfully connected to the target VM via SSH.  
- Used `nano` to open and inspect files.  
- Found flag: `THM{TEXT_EDITORS}`.

---

## Lessons Learned
- `nano` provides on-screen shortcut help (bottom of the terminal). Common keys: `Ctrl+O` (save), `Ctrl+X` (exit).  
- `vim` was introduced as a more powerful editor but requires a steeper learning curve.  
- Always confirm you’re using the correct SSH command (`ssh user@ip`) — a typo (e.g., `shh`) will fail to connect.  

---

## Tip
- If you plan to use `vim` later, try a short cheat-sheet for modes (`i` to insert, `Esc` then `:wq` to save & quit) so you don’t get stuck.
