# 📁 File Monitoring — Demo

> **SENTINEL PoC · Fictional filesystem events**

```text
┌──────────────────────────────────────────────────────────────────────┐
│                       SENTINEL :: FILES                              │
├──────────────────────────────────────────────────────────────────────┤
│ WATCH PATH     /home/demo                                            │
│ STATUS         ● ACTIVE                                              │
│ EVENTS         7                                                      │
└──────────────────────────────────────────────────────────────────────┘

 FILE ACTIVITY
 ─────────────────────────────────────────────────────────────────────

 14:25:41  + CREATED
           /home/demo/report.txt

 14:26:09  ~ MODIFIED
           /home/demo/report.txt

 14:27:02  + CREATED
           /home/demo/notes.txt

 14:27:33  → RENAMED
           notes.txt → investigation-notes.txt

 14:28:11  → MOVED
           investigation-notes.txt
           → /home/demo/archive/

 14:29:44  ~ MODIFIED
           /home/demo/config/demo.conf

 14:30:01  - DELETED
           /home/demo/temp.txt
```

### Terminal View

```text
$ sentinel files --watch /home/demo

[14:25:41] CREATED   report.txt
[14:26:09] MODIFIED  report.txt
[14:27:02] CREATED   notes.txt
[14:27:33] RENAMED   notes.txt -> investigation-notes.txt
[14:28:11] MOVED     investigation-notes.txt -> archive/
[14:29:44] MODIFIED  config/demo.conf
[14:30:01] DELETED   temp.txt

7 filesystem events recorded.
```

### Alert Example

```text
╔══════════════════════════════════════════════════════════════════════╗
║ 🚨 SENTINEL FILE ALERT                                               ║
╠══════════════════════════════════════════════════════════════════════╣
║ Event     : Configuration file modified                             ║
║ File      : /home/demo/config/demo.conf                             ║
║ Time      : 14:29:44                                                  ║
║ Severity  : MEDIUM                                                    ║
╚══════════════════════════════════════════════════════════════════════╝
```

> **Demo only:** All paths and filenames are fictional.
