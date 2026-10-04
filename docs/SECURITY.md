# 🔐 Sentinel Security

> **Security and privacy principles for the Sentinel defensive monitoring PoC.**

Sentinel is designed for **authorized defensive monitoring** of computers owned or administered by the person operating the tool.

The purpose of Sentinel is to provide visibility into security-relevant activity and help reconstruct events that occurred while a computer was unattended.

---

## 🛡️ Security Principles

### 1. Authorized Use Only

Sentinel should only be deployed on systems where the operator has appropriate authorization.

Do not use Sentinel to monitor another person's computer without their knowledge and authorization.

### 2. Security-Relevant Monitoring

Sentinel focuses on security and system activity such as:

* Authentication events
* Login and logout activity
* Failed authentication attempts
* Process execution
* File creation, modification, deletion, and movement
* Browser activity relevant to security investigation
* USB device connection and removal
* Selected configuration changes
* Security alerts

The PoC is **not intended to function as a covert keylogger or credential-stealing tool**.

### 3. No Password Collection

Sentinel should never intentionally collect or store:

* Passwords
* Authentication tokens
* Private keys
* API secrets
* Telegram bot tokens in logs
* Credit-card information
* Private message contents

Authentication monitoring should record the **event**, not the user's secret.

Example:

```text
LOGIN FAILED
User: kali
Time: 14:35:42
Reason: Authentication failure
```

Instead of recording the password that was entered.

---

## 🔑 Secret Management

Sensitive credentials must never be committed to GitHub.

Examples include:

```text
Telegram Bot Token
API Keys
Passwords
Private Keys
Cloud Credentials
Database Credentials
Session Tokens
```

Use environment variables or another secure secret-management mechanism.

Example:

```text
TELEGRAM_BOT_TOKEN=<stored securely>
```

Never place real credentials inside:

```text
README.md
FEATURES.md
SECURITY.md
screenshots/
demo/
source files committed to a public repository
```

---

## 📁 Log Protection

Monitoring logs may contain security-sensitive information such as:

```text
Usernames
Timestamps
File Paths
Process Names
Device Information
Website Domains
IP Addresses
System Events
```

Logs should therefore be protected using appropriate filesystem permissions and access controls.

Example principle:

```text
Monitor
   ↓
Event
   ↓
Sanitize
   ↓
Store Securely
   ↓
Authorized Review
```

---

## 🌐 Browser Privacy

Browser monitoring should be limited to information required for the security-monitoring purpose.

The PoC may demonstrate example information such as:

```text
Browser: Firefox
Domain: example.com
Event: Page Visit
Time: 14:22:17
```

Real private browsing data should not be uploaded to a public repository.

When publishing screenshots or demonstrations, use fictional domains and sanitized information.

---

## 📱 Telegram Security

Telegram integration can be used to send security alerts to an authorized administrator.

Example:

```text
🚨 SENTINEL SECURITY ALERT

Event: Failed Authentication
User: demo-user
Time: 14:35:42
Host: DEMO-PC

Review required.
```

The Telegram bot token must remain private.

If a token is accidentally exposed:

1. Revoke the compromised token.
2. Generate a new token.
3. Remove the secret from the repository.
4. Check repository history if necessary.
5. Update the local configuration securely.

---

## 🔄 Startup & Persistence

Sentinel may be configured to start automatically after system restart.

This is intended to maintain **authorized security monitoring** without requiring the administrator to manually start the application after every reboot.

Automatic startup should always be visible to the system administrator and configured according to the operating system's security policies.

---

## 🧩 Least Privilege

Sentinel should operate with the minimum privileges necessary for the monitoring functions being used.

Avoid running the entire application as `root` or Administrator when elevated privileges are not required.

Recommended principle:

```text
Minimum Privileges
       ↓
Required Monitoring
       ↓
Reduced Attack Surface
```

---

## 🧪 PoC Security Status

This repository contains a **proof of concept**.

It should not automatically be considered production-ready.

Before production deployment, additional security work should include:

* Strong access control
* Secure log storage
* Log integrity protection
* Secret management
* Configuration hardening
* Permission auditing
* Secure update mechanisms
* Alert authentication
* Data-retention policies
* Privacy review
* OS-specific security testing

---

## 🚨 Responsible Use

Sentinel is intended for:

* Personal computer security
* Defensive security research
* Authorized system administration
* Incident investigation
* Security demonstrations
* Security-awareness testing

It must not be used for:

* Unauthorized surveillance
* Credential theft
* Password collection
* Covert keylogging
* Unauthorized access
* Monitoring systems without permission

---

## 🔒 Security Goal

The goal of Sentinel is simple:

> **Provide useful security visibility without turning the monitoring system into a credential or privacy harvesting tool.**
