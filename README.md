# Day-22-100-Days-challenge-in-cybersecurity-
## 🗓️ Day 22: Web Enumeration & Misconfigurations

**Topic:** Directory Brute-Forcing & Sensitive Data Exposure

### 📝 Summary
Day 22 focused on enumerating hidden content on a target web server. The objective was to identify administrative entry points and sensitive files that were accessible due to weak server configurations.

### 🛠️ Methodology
* **Technique:** Directory Brute-Forcing (Fuzzing)
* **Tools Used:** `Gobuster`, `FFUF`, or `Dirb`
* **Wordlist:** `directory-list-2.3-medium.txt` (SecLists)

### 🚩 Findings
1.  **Hidden Admin Panels:**
    * Discovered `/admin` and `/dashboard` endpoints returning `200 OK`.
    * *Risk:* Exposed login interfaces allow for credential stuffing or brute-force attacks.
2.  **Sensitive Information Disclosure:**
    * Found `config.php.bak` and `.env` files.
    * *Content:* Database credentials and API keys.
3.  **Misconfiguration:**
    * Directory listing was enabled on `/images/`, revealing file structure.

### 🛡️ Mitigation
* **Disable Directory Listing:** Ensure `Options -Indexes` is set in Apache (or equivalent in Nginx).
* **Access Control:** Block public access to sensitive file extensions (e.g., `.git`, `.bak`, `.config`).
* **Standardization:** Avoid "Security by Obscurity"; implement proper 403 Forbidden rules for administrative paths.
