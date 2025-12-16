# 🧱 Lab Architecture

## Overview

This lab simulates a **basic SOC SIEM environment** using **Splunk Enterprise** to collect and analyze logs from multiple hosts. The goal is to demonstrate an understanding of **SIEM architecture**, **log ingestion**, and **host-based monitoring** in a lab environment.

---

## Architecture Layout

| Component                | Purpose                                                           |
| ------------------------ | ------------------------------------------------------------------|
| Splunk Enterprise Server | Central SIEM platform used to ingest, index, and analyze logs     |
| Linux Host               | Acts as a log source and Splunk server                            |
| Windows Host(Forwarder)  | Acts as the Universal Forwarder sending logs to the Splunk Server |
---

## Logical Architecture Diagram

> *(Insert diagram image here)*

**Log Flow:**

```
[Linux Host Logs] ─┐
                   ├──> [Splunk Enterprise Server : Port 9997]
[Windows Logs] ────┘
```

📌 *This mirrors a real-world SOC setup where endpoints forward logs to a centralized SIEM for correlation and analysis.*

---

## Virtual Machines & Operating Systems

| Machine | OS             | Role                                  |
| ------- | -------------- | ------------------------------------- |
| VM 1    | Linux (Ubuntu) | Splunk Host Server + Log Source |
| VM 2    | Windows        | Log Source (Event Logs)               |

---

## Network Configuration

* VMs connected via: `NAT / Internal Network`
* Communication occurs over:

  * **Splunk Web:** TCP 8000
  * **Splunk Forwarding:** TCP 9997
* All log traffic is sent **inbound to the Splunk server**

📌 *This simulates internal enterprise log forwarding where endpoints do not expose external services.*

---

## Data Flow Explanation

1. Logs are generated on Linux and Windows systems
2. Universal Forwarders collect system and event logs
3. Logs are securely forwarded to the Splunk Enterprise server
4. Splunk indexes and makes data searchable via Splunk Web

---

## Why This Architecture Was Chosen

* Reflects **real SOC environments**
* Separates **log sources** from **analysis platform**
* Scalable (additional hosts can be added easily)
* Aligns with enterprise SIEM best practices

---

## Security Relevance

This architecture enables:

* Centralized visibility across multiple systems
* Event correlation between hosts
* Detection of suspicious activity such as authentication failures or system changes

---

## Future Improvements

* Add alerting rules for failed logins
* Create dashboards for authentication activity
* Introduce additional log sources (firewall, web server)
* Enable TLS encryption between forwarders and Splunk

---

## Evidence & Screenshots

**Recommended screenshots for this section:**

* VM overview showing both systems running
* Network configuration page
* Splunk listening port configuration
* Architecture diagram (simple is fine)

---

### ✅ Tip for GitHub

Name the diagram something like:

```
architecture_diagram.png
```

and reference it in markdown:

```
![SOC Lab Architecture](architecture_diagram.png)
```

---

If you want, next I can:

* Create a **matching diagram image**
* Review your README and integrate this cleanly
* Create templates for #2 and #3 so everything matches stylistically

You’re building a **real portfolio**, not just finishing a lab — and this template reflects that.
