<div align="center">

# 🛡️ Sentinel

### Defensive System Activity Monitoring — PoC

**A cross-platform security monitoring tool for investigating what happened on a computer while it was unattended.**

<br>

![Linux](https://img.shields.io/badge/Linux-Supported-FCC624?style=for-the-badge\&logo=linux\&logoColor=black)
![Windows](https://img.shields.io/badge/Windows-Supported-0078D4?style=for-the-badge\&logo=windows\&logoColor=white)
![PoC](https://img.shields.io/badge/Project-PoC-orange?style=for-the-badge)
![Security](https://img.shields.io/badge/Focus-Defensive%20Security-red?style=for-the-badge)

</div>

---

## 🔎 About

**Sentinel** is a personal defensive-security tool designed to provide visibility into activity occurring on a computer when the owner is away.

The tool creates an activity timeline from multiple security-relevant sources, allowing the owner to investigate events such as:

* 🔐 User logins and authentication events
* 🌐 Browser activity
* 📁 File creation, modification, and deletion
* ⚙️ Process/program execution
* 🔌 USB device activity
* 🛠️ Configuration changes
* 🚨 Security alerts
* 🔄 Activity after system restart

The project is currently presented as a **Proof of Concept (PoC)** demonstrating the monitoring and alerting capabilities of the tool.

---

# 🎯 The Idea

The concept behind Sentinel is simple:

> **If someone uses my computer while I'm away, I want to know what happened.**

Instead of relying on a single source of information, Sentinel combines multiple event types into a chronological activity history.

```text
                 🖥️ COMPUTER
                      │
       ┌──────────────┼──────────────┐
       │              │              │
       ▼              ▼              ▼
    🔐 LOGIN       📁 FILES       ⚙️ PROCESS
       │              │              │
       ├──────────────┼──────────────┤
       │              │              │
       ▼              ▼              ▼
   🌐 BROWSER       🔌 USB        🛠️ CONFIG
       │              │              │
       └──────────────┼──────────────┘
                      ▼
               🚨 EVENT ENGINE
                      │
              ┌───────┴───────┐
              ▼               ▼
          📊 LOGS        📱 TELEGRAM
```

---

# ✨ What Sentinel Monitors

## 🔐 Login & Session Activity

Sentinel can record security-relevant authentication and session events.

Examples:

```text
LOGIN SUCCESS
LOGIN FAILED
LOGOUT
SESSION START
SESSION END
```

Information can include:

* Username
* Event type
* Timestamp
* Session information
* Authentication status

Example:

```text
🔐 LOGIN EVENT

User: kali
Status: SUCCESS
Time: 14:21:03
```

---

## 🌐 Browser Activity

Sentinel can monitor supported browser activity to help reconstruct browsing activity.

Supported browsers can include:

* Firefox
* Chrome
* Brave

Possible information:

```text
Website
Search activity
Browser
Timestamp
```

Example:

```text
🌐 BROWSER EVENT

Browser: Firefox
Action: VISITED
Website: google.com
Time: 14:22:17
```

---

## 📁 File Activity

Sentinel can detect changes to monitored files and directories.

```text
CREATE
MODIFY
DELETE
RENAME
MOVE
```

Example:

```text
📁 FILE EVENT

Action: CREATED
File: /home/user/test.txt
Time: 14:25:41
```

This helps identify unexpected changes made while the computer was unattended.

---

## ⚙️ Process Activity

The tool can monitor relevant process/program activity.

```text
▶ PROCESS STARTED
⏹ PROCESS STOPPED
```

Example:

```text
⚙️ PROCESS EVENT

Process: firefox
User: kali
Action: STARTED
Time: 14:31:10
```

---

## 🔌 USB Activity

Sentinel can detect removable-device activity.

```text
🔌 USB CONNECTED
🔌 USB REMOVED
```

Example:

```text
🔌 USB EVENT

Device: USB Storage
Action: CONNECTED
Time: 14:32:18
```

This can help identify whether an external device was connected while the system was unattended.

---

## 🛠️ Configuration Changes

The tool can monitor selected configuration files and security-related settings.

Example:

```text
🚨 CONFIGURATION CHANGE

File: /etc/example/config.conf
Action: MODIFIED
Time: 14:35:42
```

This allows unexpected configuration changes to become visible during an investigation.

---

# 🚨 Alert System

When an important event occurs, Sentinel can generate a security alert.

Example:

```text
╔══════════════════════════════════╗
║       🚨 SECURITY ALERT          ║
╠══════════════════════════════════╣
║                                  ║
║ Configuration changed            ║
║                                  ║
║ File: config.conf                ║
║ Time: 14:35:42                   ║
║                                  ║
╚══════════════════════════════════╝
```

---

# 📱 Telegram Integration

One of the features of Sentinel is **Telegram integration**.

The tool can communicate with a Telegram bot to provide the owner with security notifications and authorized monitoring controls.

### Notifications

Possible alerts include:

```text
🔐 Login detected
❌ Failed authentication
🌐 Browser activity
📁 Important file change
🔌 USB connected
⚙️ Configuration changed
⚙️ Process activity
🚨 Security event
```

Example:

```text
🚨 SENTINEL ALERT

🔐 New Login Detected

User: kali
Status: SUCCESS
Time: 14:21:03
```

Telegram integration allows the owner to receive important events without continuously watching the local machine.

---

# 🔄 After Restart

Sentinel is designed to continue monitoring after the computer is restarted.

```text
       🖥️ RESTART
           │
           ▼
      ⚡ SYSTEM BOOT
           │
           ▼
     🛡️ SENTINEL START
           │
           ▼
    MONITORING INITIALIZED
           │
      ┌────┼────┐
      ▼    ▼    ▼
     🔐   📁   ⚙️
     LOGIN FILE PROCESS
           │
           ▼
       🚨 ALERT
           │
           ▼
       📱 TELEGRAM
```

This allows the PoC to demonstrate persistent monitoring across system restarts.

---

# 🖥️ Cross-Platform

Sentinel is designed for:

| Platform   | Support |
| ---------- | :-----: |
| 🐧 Linux   |    ✅    |
| 🪟 Windows |    ✅    |

The underlying monitoring mechanisms can differ between operating systems.

---

# 📊 Example Activity Timeline

A single investigation can produce a timeline such as:

```text
14:21:03  🔐 LOGIN SUCCESS
14:22:17  🌐 BROWSER ACTIVITY
14:25:41  📁 FILE CREATED
14:28:09  🔌 USB CONNECTED
14:30:55  ⚙️ CONFIG MODIFIED
14:31:10  ▶️ PROCESS STARTED
14:35:42  ❌ AUTHENTICATION FAILED
14:36:02  🚨 SECURITY ALERT
```

This timeline is the core idea behind the project:

**collect → correlate → alert → investigate**

---

# 🧩 How It Works

```text
┌───────────────────────────────────────────────┐
│                SENTINEL AGENT                 │
└───────────────────────┬───────────────────────┘
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
     🔐 Auth          📁 Files        ⚙️ Process
        │               │               │
        └───────────────┼───────────────┘
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
     🌐 Browser       🔌 USB          🛠️ Config
        │               │               │
        └───────────────┼───────────────┘
                        │
                        ▼
                ┌──────────────┐
                │ EVENT ENGINE │
                └───────┬──────┘
                        │
                 ┌──────┴──────┐
                 ▼             ▼
              📊 LOGS      🚨 ALERTS
                               │
                               ▼
                          📱 TELEGRAM
```

---

# 🎥 Proof of Concept

This repository contains a **PoC of Sentinel**, rather than the complete production implementation.

The PoC demonstrates the core concept and selected monitoring capabilities.

### Suggested Demo

The PoC demonstration can show:

```text
1. Start Sentinel
2. Login/session event occurs
3. Open a browser
4. Visit a website
5. Create/modify a file
6. Start a process
7. Connect a USB device
8. Change a monitored configuration
9. Generate security events
10. Receive the corresponding Telegram alert
11. Restart the computer
12. Verify Sentinel starts again
13. Credential saving autoamtically
14. keyboard listener what he is typing 
15. Connected usb data copy 
```

---

# 📸 Screenshots

Add screenshots from the actual PoC here.

### 🖥️ Sentinel Interface

```text
docs/sentinel-dashboard.png
```

![Sentinel Dashboard](docs/sentinel-dashboard.png)

### 🚨 Security Alerts

```text
docs/security-alerts.png
```

![Security Alerts](docs/security-alerts.png)

### 📊 Activity Timeline

```text
docs/activity-timeline.png
```

![Activity Timeline](docs/activity-timeline.png)

### 📱 Telegram

```text
docs/telegram-alert.png
```

![Telegram Alert](docs/telegram-alert.png)

---

# 🔒 Privacy & Security

Sentinel is intended for **defensive monitoring of systems owned by the operator or systems where monitoring has been explicitly authorized**.

The project focuses on security-relevant events rather than covert collection of arbitrary personal information.

The monitoring system should not be used to collect:

* Passwords
* Authentication secrets
* Private messages
* Arbitrary keystrokes

Logs may contain sensitive information such as URLs, usernames, file paths, process information, device information, and timestamps. These logs should therefore be protected appropriately.

---

# ⚠️ PoC Status

This project is a **Proof of Concept**.

It is intended to demonstrate the technical concept and monitoring workflow.

It should not be considered a complete enterprise endpoint-detection platform.

Some capabilities may have limitations depending on:

* Operating system
* OS version
* User permissions
* Browser configuration
* Security settings
* System logging configuration
* Application behavior

---

# ⚖️ Responsible Use

Sentinel is designed for:

* 🛡️ Defensive security
* 🔎 Incident investigation
* 💻 Personal computer security
* 🧪 Authorized security research
* 🏢 System administration
* 📊 Security auditing

**Only use Sentinel on systems you own or are explicitly authorized to monitor.**

Do not use the project for unauthorized surveillance, credential collection, or privacy violations.

---

# 📜 License

This PoC is released under the **MIT License**.

See [`LICENSE`](LICENSE) for details.

---

<div align="center">

## 🛡️ Sentinel

### **Visibility when you're away.**

**Defensive monitoring • Activity auditing • Security alerts**

<br>

`Linux` • `Windows` • `Telegram` • `Security Monitoring`

<br>

**⚠️ Use responsibly.**

</div>
