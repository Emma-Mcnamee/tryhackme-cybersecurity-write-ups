# Downloading Files (wget) — TryHackMe
**Difficulty:** Easy  
**Time:** ~15–20 minutes  
**Goal:** Host a file using Python’s HTTP server and download it using `wget`.

---

## Summary
In this lab, I practiced serving files from a deployed Linux instance using Python’s built-in `http.server` and downloading files using `wget` from another terminal. I learned how to troubleshoot connection issues caused by incorrect IP addresses.

---

## Tools Used
- TryHackMe Attack Box and deployed Linux VM  
- Commands: `ssh`, `python3 -m http.server`, `wget`, `cat`

---

## Steps / Playbook

1. **Connect to the deployed instance**
   - Opened a terminal in the Attack Box. Initially logged in as `root`.  
   - Connected to the deployed instance:
     ```bash
     ssh tryhackme@10.201.43.112
     ```
   - Entered the provided THM password to log in.  

2. **Start a Python HTTP server**
   - From the home directory of `tryhackme`, started the server:
     ```bash
     python3 -m http.server
     ```
   - Server started on port `8000`, serving files from the home directory.

3. **Download the file using `wget`**
   - Opened a second terminal as `root`.  
   - Attempted to download the file:
     ```bash
     wget http://10.20.43.112:8000/.flag.txt
     ```
   - Connection failed because the IP address was incorrect. Corrected the command:
     ```bash
     wget http://10.201.43.112:8000/.flag.txt
     ```
   - File `.flag.txt` was successfully downloaded.

4. **Find the flag**
   - Displayed the contents of the downloaded file:
     ```bash
     cat .flag.txt
     ```
   - Flag revealed:
     ```
     THM{WGET_WEBSERVER}
     ```

---

## Results
- Successfully served files using Python’s HTTP server.  
- Downloaded `.flag.txt` from the deployed instance using `wget`.  
- Flag obtained: `THM{WGET_WEBSERVER}`.

---

## Lessons Learned
- `wget` requires the correct IP address and port to download files.  
- Using multiple terminals allows simultaneous server hosting and file retrieval.  
- Always double-check commands for typos — even small errors (like `10.20.43.112` instead of `10.201.43.112`) can prevent connections.

---

## Tips
- To stop the Python server, press `Ctrl+C` in the terminal where it’s running.  
- You can use `wget -O <filename>` to save the file with a custom name.
