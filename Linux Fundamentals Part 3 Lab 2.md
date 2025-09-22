# Intro to Python3 & http.server — TryHackMe
**Difficulty:** Easy  
**Time:** ~20 minutes  
**Goal:** Host a simple HTTP server with Python and retrieve a file from it using `wget`.

---

## Summary
In this lab I practiced using Python's built-in `http.server` to serve files from a directory and used `wget` from a separate terminal/machine to download a hidden file. The exercise shows how simple it is to transfer files over HTTP from a host machine to an attacker/another machine.

---

## Tools Used
- TryHackMe Attack Box and target Linux VM  
- Commands: `whoami`, `python3 -m http.server`, `wget`, `cat`

---

## Steps / Playbook

1. **Verify login**
   - Confirmed I was logged into the target machine as `tryhackme`:
     ```bash
     whoami
     ```
   - Verified remote IP/session: `10.201.55.158` (target VM).

2. **Start a simple HTTP server**
   - From the `tryhackme` home directory started a Python HTTP server:
     ```bash
     python3 -m http.server
     ```
   - Output indicated the server was running on port `8000`.

3. **Download file from another terminal**
   - Opened a second terminal on the Attack Box (not logged into the target VM). The attack box prompt showed: `root@ip-10-21-38-129`.
   - Downloaded the hidden file using `wget`:
     ```bash
     wget http://10.201.55.158:8000/.flag.txt
     ```
   - The file `.flag.txt` was saved to the current directory on the attack box.

4. **View the downloaded file**
   - Displayed the file contents:
     ```bash
     cat .flag.txt
     ```
   - Found the lab flag:
     ```
     THM{WGET_WEBSERVER}
     ```

---

## Results
- Successfully hosted files using Python's `http.server`.  
- Retrieved `.flag.txt` from the target VM using `wget`.  
- Confirmed flag: `THM{WGET_WEBSERVER}`.

---

## Lessons Learned
- `python3 -m http.server` quickly serves files over HTTP from the current directory (default port 8000).  
- Files served this way can be fetched by other machines on the same network using tools like `wget` or `curl`.  
- Always be aware of what files are in a directory before starting a server — hidden files (like `.flag.txt`) can be exposed unintentionally.

---

## References / Tips
- To stop the Python server, press `Ctrl+C` in the terminal where it’s running.  
- Use `python3 -m http.server 8080` to run the server on a different port if needed.
