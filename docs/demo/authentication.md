# 🔐 Authentication Monitoring — Demo

> **SENTINEL PoC · Fictional demonstration data**

```text
┌──────────────────────────────────────────────────────────────────────┐
│                         SENTINEL :: AUTH                             │
├──────────────────────────────────────────────────────────────────────┤
│ STATUS     ● MONITORING                                             │
│ HOST       DEMO-WORKSTATION                                        │
│ USER       demo-user                                                │
│ PLATFORM   Linux / PoC                                              │
└──────────────────────────────────────────────────────────────────────┘

 AUTHENTICATION TIMELINE
 ─────────────────────────────────────────────────────────────────────

 14:18:02  ● SESSION START
           User: demo-user

 14:21:03  ✓ LOGIN SUCCESS
           User: demo-user
           Session: SESSION-0042

 14:34:17  ⚠ LOGIN FAILED
           User: demo-user
           Reason: Authentication failure

 14:34:29  ⚠ LOGIN FAILED
           User: demo-user
           Reason: Authentication failure

 14:35:42  🚨 SECURITY ALERT
           Multiple failed authentication attempts detected

 14:36:02  ✓ LOGIN SUCCESS
           User: demo-user
           Session: SESSION-0043
```

### Event Information

| Time     | Event             | Status  |
| -------- | ----------------- | ------- |
| 14:21:03 | Login success     | Normal  |
| 14:34:17 | Login failed      | Warning |
| 14:34:29 | Login failed      | Warning |
| 14:35:42 | Multiple failures | Alert   |
| 14:36:02 | Login success     | Normal  |

### Investigation Example

```text
$ sentinel events --type authentication

[14:21:03] LOGIN_SUCCESS   user=demo-user
[14:34:17] LOGIN_FAILED    user=demo-user
[14:34:29] LOGIN_FAILED    user=demo-user
[14:35:42] ALERT            repeated authentication failures
[14:36:02] LOGIN_SUCCESS   user=demo-user
```

> **Demo only:** usernames, timestamps, sessions, and events shown above are fictional.
