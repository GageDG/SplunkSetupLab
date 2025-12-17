# 🔧 Installation & Configuration

## Overview

This document outlines the installation verification and configuration steps performed to deploy **Splunk Enterprise** and integrate log sources within a SOC-style lab environment.

> **Note:** Splunk Enterprise installer was pre-downloaded on the Linux host as part of the lab environment due to not having an internet connection.

---

## 1. Splunk Installation Verification (Linux)

### Objective

Install Splunk enterprise and ensure that it is properly running.

### Steps Taken in executed order

1. CD into the downloads folder were the Splunk Installer was located
2. Once in the proper directory I gave myself sudo permissions then executed the install command (_tar xvzf splunk_installer.tgz_)
3. The install was succesful so I moved the installed folder to the recommended 'opt' directory using the (_mv splunk /opt/_) command
4. I navigated to the new location using (_cd /opt/splunk/bin_) then executed the run command (_./splunk start --accept-license_)
5. Once the setup process was completed Splunk required a username where I used (splunkadmin) for testing purposes.
6. I completed the setup process by entering a password, after which the service came online.

### Commands Used

```bash
sudo su
tar xvzf splunk_installer.tgz
mv splunk /opt/
cd /opt/splunk/bin
./splunk start --accept-license
```

### Expected Result

* Splunk service starts successfully
* Web interface becomes accessible on port `8000`

📸 **Screenshot:** Terminal showing successful Splunk startup

---

## 2. Accessing Splunk Web Interface

### Objective

Confirm Splunk Web is reachable and functional.

* Accessed Splunk Web at:

  ```
  http://<splunk-server-ip>:8000
  ```
* Logged in using admin credentials

📸 **Screenshot:** Splunk Enterprise login page

---

## 3. Splunk Configuration (Server)

### Listening Port Configuration

Configured Splunk to receive forwarded logs on TCP port `9997`.

* Settings → Forwarding and Receiving → Configure Receiving

📸 **Screenshot:** Receiving port configuration

---

## 4. Universal Forwarder Installation

### Objective

Install and configure Universal Forwarder on log source hosts.

#### Windows Host

* Installed Splunk Universal Forwarder
* Configured to forward logs to Splunk server

#### Linux Host (if applicable)

* Installed forwarder package
* Configured forwarding destination

📸 **Screenshot:** Forwarder installation confirmation

---

## 5. Log Source Configuration

### Windows Event Logs

* Configured forwarder to ingest:

  * Security
  * System
  * Application logs

📸 **Screenshot:** Windows logs appearing in Splunk

---

## 6. Verification & Validation

### Objective

Ensure logs are successfully ingested and searchable.

### Search Used

```spl
index=* | stats count by host
```

### Result

* Logs visible from both Linux and Windows hosts
* Hostnames correctly identified

📸 **Screenshot:** Splunk search results showing multiple hosts

---

## 7. Troubleshooting & Challenges

### Issues Encountered

* Service startup delays
* Initial port connectivity issues

### Resolutions

* Restarted Splunk service
* Verified firewall and listening ports

📸 **Screenshot:** Error message and resolution confirmation

---

## 8. Skills Demonstrated

* SIEM deployment and configuration
* Log ingestion via Universal Forwarders
* Splunk search and validation
* Troubleshooting service and network issues
* SOC-style documentation practices

---

## When to Split Files Later

Only split into:

* `INSTALLATION.md`
* `CONFIGURATION.md`

**If** you add:

* Multiple data sources
* Dashboards
* Alerts
* Detection engineering

For now — **keep it together**.

---

## Final Verdict

✔ One combined file
✔ Clear separation inside
✔ Transparent about pre-install
✔ Perfect for resume + interviews

If you want next, I can:

* Review your current README and align wording
* Help you phrase this **exactly** how SOC interviewers expect
* Create a **Detection & Analysis** template (huge resume boost)

You’re building this the *right* way.
