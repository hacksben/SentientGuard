# ⚙️ Process Monitoring — Demo

> **SENTINEL PoC · Fictional process events**

```text
┌──────────────────────────────────────────────────────────────────────┐
│                      SENTINEL :: PROCESSES                           │
├──────────────────────────────────────────────────────────────────────┤
│ STATUS      ● MONITORING                                             │
│ HOST        DEMO-WORKSTATION                                        │
│ EVENTS      8                                                        │
└──────────────────────────────────────────────────────────────────────┘

 PROCESS TIMELINE
 ─────────────────────────────────────────────────────────────────────

 TIME       PID     EVENT       PROCESS
 ─────────────────────────────────────────────────────────────────────
 14:21:10   2041    START       desktop-session
 14:22:02   2187    START       firefox
 14:23:15   2312    START       terminal
 14:25:09   2451    START       file-manager
 14:26:41   2312    STOP        terminal
 14:28:03   2678    START       demo-editor
 14:30:14   2451    STOP        file-manager
 14:31:10   2811    START       demo-application
```

### Terminal View

```text
$ sentinel processes --follow

14:21:10  START  PID=2041  desktop-session
14:22:02  START  PID=2187  firefox
14:23:15  START  PID=2312  terminal
14:25:09  START  PID=2451  file-manager
14:26:41  STOP   PID=2312  terminal
14:28:03  START  PID=2678  demo-editor
14:30:14  STOP   PID=2451  file-manager
14:31:10  START  PID=2811  demo-application
```

### Activity Correlation

```text
LOGIN SUCCESS
      │
      ▼
Firefox Started
      │
      ▼
Browser Activity
      │
      ▼
File Manager Started
      │
      ▼
File Activity
      │
      ▼
Security Event
```

> **Demo only:** Process names, PIDs, timestamps, and events are fictional.
