# 🛡️ Sentinel Features

> **A defensive activity-monitoring PoC for investigating what happened on an unattended computer.**

Sentinel combines multiple security-relevant event sources into a single activity picture.

---

## ✨ Feature Overview

| Feature               | Description                                                        |
| --------------------- | ------------------------------------------------------------------ |
| 🔐 Authentication     | Track login, logout, and failed authentication events              |
| 🌐 Browser Activity   | Demonstrate security-relevant website/search activity              |
| 📁 File Monitoring    | Detect file creation, modification, deletion, rename, and movement |
| ⚙️ Process Monitoring | Track programs and processes starting or stopping                  |
| 🔌 USB Monitoring     | Detect USB device connection and removal                           |
| 🚨 Security Alerts    | Generate alerts for important or suspicious events                 |
| 📱 Telegram           | Deliver authorized security notifications                          |
| 🔄 Auto Startup       | Continue monitoring after system restart                           |
| 🖥️ Cross Platform    | Designed with Linux and Windows support in mind                    |

---

# 🔐 Authentication Monitoring

Sentinel can record authentication-related events.

Example events:

```text
LOGIN SUCCESS
LOGIN FAILED
LOGOUT
SESSION START
SESSION END
REMOTE LOGIN
```

Example event:

```text
┌──────────────────────────────────────────┐
│ 🔐 AUTHENTICATION EVENT                  │
├──────────────────────────────────────────┤
│ User      : demo-user                    │
│ Event     : LOGIN SUCCESS                │
│ Time      : 14:21:03                     │
│ Session   : SESSION-0042                 │
└──────────────────────────────────────────┘
```

This helps determine **when an account was accessed** and what happened around that event.

---

# 🌐 Browser Activity

The PoC can demonstrate browser-related security events.

Supported browser examples:

```text
Firefox
Chrome
Brave
```

Example information:

```text
Browser
Domain
Event Type
Timestamp
```

Example:

```text
14:22:17  Firefox  example.com       PAGE VISIT
14:23:41  Chrome   search.example    SEARCH
14:24:08  Brave    docs.example      PAGE VISIT
```

> Demo data is fictional and is included only to demonstrate the interface.

---

# 📁 File Activity

Sentinel can monitor important filesystem activity.

Example events:

```text
FILE CREATED
FILE MODIFIED
FILE DELETED
FILE RENAMED
FILE MOVED
```

Example:

```text
14:25:41  CREATED   /home/demo/report.txt
14:26:09  MODIFIED  /home/demo/report.txt
14:27:33  RENAMED  /home/demo/report.txt
```

This can help identify changes that occurred during an investigation.

---

# ⚙️ Process Monitoring

Sentinel can track process-related events.

Example:

```text
PROCESS START
PROCESS STOP
```

Example:

```text
14:31:10  PROCESS STARTED
Process: firefox
User: demo-user

14:32:44  PROCESS STARTED
Process: terminal
User: demo-user
```

Process events can be correlated with authentication, browser, file, and other activity.

---

# 🔌 USB Monitoring

Sentinel can detect USB device events.

Example:

```text
USB CONNECTED
USB REMOVED
```

Example:

```text
┌──────────────────────────────────────────┐
│ 🔌 USB DEVICE EVENT                     │
├──────────────────────────────────────────┤
│ Event     : DEVICE CONNECTED             │
│ Device    : Demo USB Storage             │
│ Time      : 14:28:09                     │
│ Status    : Detected                     │
└──────────────────────────────────────────┘
```

This can help identify removable-device activity during an investigation.

---

# 🚨 Security Alerts

Important events can be promoted into security alerts.

Example alert sources:

```text
Failed Authentication
Unexpected Process
Important File Change
USB Connection
Configuration Change
Repeated Security Events
```

Example:

```text
╔══════════════════════════════════════════╗
║          🚨 SECURITY ALERT              ║
╠══════════════════════════════════════════╣
║ Event : Multiple Failed Logins           ║
║ User  : demo-user                        ║
║ Time  : 14:35:42                         ║
║ Risk  : HIGH                             ║
╚══════════════════════════════════════════╝
```

---

# 📱 Telegram Notifications

Sentinel can integrate with Telegram for authorized security notifications.

Example:

```text
🚨 SENTINEL

Security Alert

Event:
Multiple Failed Authentication Attempts

Host:
DEMO-PC

Time:
14:35:42

Action:
Review activity timeline
```

Sensitive credentials and bot tokens should never be included in logs or public documentation.

---

# 🔄 Automatic Startup

Sentinel can be configured to start after system reboot.

Example lifecycle:

```text
SYSTEM START
     │
     ▼
SENTINEL START
     │
     ▼
MONITORING ENGINE
     │
     ├── Authentication
     ├── Browser
     ├── Files
     ├── Processes
     ├── USB
     └── Security Events
             │
             ▼
        ALERT ENGINE
             │
             ▼
          Telegram
```

---

# 🔎 Event Correlation

The main value of Sentinel is not just collecting individual events.

Events can be viewed as a timeline:

```text
14:21:03  🔐 LOGIN SUCCESS
14:22:17  🌐 BROWSER ACTIVITY
14:25:41  📁 FILE CREATED
14:28:09  🔌 USB CONNECTED
14:30:55  ⚙️ CONFIGURATION CHANGE
14:31:10  ⚙️ PROCESS STARTED
14:35:42  🚨 AUTHENTICATION FAILED
```

This creates a simple investigation timeline showing **what happened and when**.

---

# 🧪 PoC Scope

The repository demonstrates the concept and interface of Sentinel.

Some features may require different implementations depending on:

* Operating system
* OS version
* User permissions
* Browser configuration
* Security policies
* Available system APIs

The PoC should therefore be treated as a **research and demonstration project**, not a finished enterprise monitoring platform.

---

# 🎯 Project Goal

Sentinel aims to answer a simple defensive-security question:

> **"What happened on my computer while I was away?"**

By combining authentication, browser, filesystem, process, USB, and security events, Sentinel provides a structured activity timeline for investigation.
