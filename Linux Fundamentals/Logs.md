# Linux Fundamentals — Apache2 Logs (Final Lab)
**Difficulty:** Easy  
**Time:** ~10–20 minutes  
**Goal:** Locate Apache2 log files on the deployed Linux machine and determine which IP visited the website and what resource was requested.

---

## Summary
In this lab I located Apache2 log files under `/var/log`, inspected a rotated access log, and identified the IP address that visited the website and the specific file requested.

---

## Tools Used
- TryHackMe Attack Box and deployed Linux VM  
- Commands: `ssh`, `cd`, `ls -lah`, `cat`, `grep`, `tail`, `sudo` (if available)  
- External resources: quick web searches for log file locations and reading `/proc` when necessary

---

## Steps / Playbook

1. **Connect to deployed instance**
   - SSH'd into the target machine as the provided user:  
     ```bash
     ssh user@<target-ip>
     ```

2. **Navigate to logs directory**
   - Changed directory to the system logs folder:
     ```bash
     cd /var/log
     ```

3. **List available log files**
   - Listed files to see Apache logs:
     ```bash
     ls -lah
     ```
   - Observed log files such as:
     ```
     access.log
     access.log.1
     error.log
     error.log.1
     error.log.2
     other_vhosts_access.log
     ```

4. **Attempt to read active access log**
   - Tried to read `access.log` and received permission denied (typical when owned by `root` or `www-data`):
     ```bash
     cat access.log    # -> Permission denied
     ```

5. **Read rotated access log**
   - Read the rotated log file which was readable:
     ```bash
     cat access.log.1
     ```
   - Found the raw log entry:
     ```
     10.9.232.111 - - [04/May/2021:18:18:16 +0000] "GET /catsanddogs.jpg HTTP/1.1" 200 51395 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36"
     ```

6. **Extract and verify visitor info**
   - Identified the IP and resource directly from the log entry:
     - IP: `10.9.232.111`
     - Resource: `/catsanddogs.jpg`

---

## Results
- Located Apache logs in `/var/log`.
- Read `access.log.1` and found a successful GET for `/catsanddogs.jpg`.
- **Final answer (lab requirement):**
  - **IP address that visited the website:** `10.9.232.111`
  - **File accessed:** `/catsanddogs.jpg`

---

## Lessons Learned
- Active `access.log` may be permission-protected and require `sudo` to read.  
- Rotated logs (`access.log.1`, `access.log.2`, `.gz`) are often accessible without elevated privileges.  
- Apache log entries follow the Common Log Format and contain IP, timestamp, request, status, response size, referer, and user-agent.  
- Use `grep` to quickly search logs for IPs or filenames.

---

## Suggested Verification / Follow-Up Commands (Cheat Sheet)
```bash
# check file ownership & permissions
ls -l /var/log/access.log /var/log/access.log.1

# search rotated and active logs for IP or filename
grep "10.9.232.111" /var/log/*access* -n
grep "catsanddogs.jpg" /var/log/*access* -n

# if you have sudo, read live log entries
sudo tail -n 200 /var/log/apache2/access.log
sudo tail -f /var/log/apache2/access.log

# if logs are in /var/log (not apache2), adjust paths accordingly
grep "string" /var/log/*access* -n
