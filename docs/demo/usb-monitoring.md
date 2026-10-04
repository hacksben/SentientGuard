# 🔌 USB Monitoring — Demo

> **SENTINEL PoC · Fictional USB device events**

```text
┌──────────────────────────────────────────────────────────────────────┐
│                         SENTINEL :: USB                              │
├──────────────────────────────────────────────────────────────────────┤
│ STATUS       ● MONITORING                                            │
│ DEVICE COUNT 2                                                       │
│ EVENTS       4                                                       │
└──────────────────────────────────────────────────────────────────────┘

 USB DEVICE TIMELINE
 ─────────────────────────────────────────────────────────────────────

 14:28:09  + DEVICE CONNECTED
           Device: Demo USB Storage
           Type: Storage
           Status: Mounted

 14:28:16  ✓ DEVICE READY
           Device: Demo USB Storage
           Mount: /media/demo/USB

 14:33:47  - DEVICE REMOVED
           Device: Demo USB Storage

 14:34:02  + DEVICE CONNECTED
           Device: Demo USB Device
           Type: Storage
           Status: Detected
```

### Terminal View

```text
$ sentinel usb --monitor

[14:28:09] USB_CONNECTED
           Demo USB Storage

[14:28:16] USB_READY
           /media/demo/USB

[14:33:47] USB_REMOVED
           Demo USB Storage

[14:34:02] USB_CONNECTED
           Demo USB Device
```

### Security Event

```text
┌──────────────────────────────────────────────────────────────────────┐
│ ⚠ USB ACTIVITY DETECTED                                              │
├──────────────────────────────────────────────────────────────────────┤
│ Device    : Demo USB Storage                                        │
│ Event     : Connected                                                │
│ Time      : 14:28:09                                                 │
│ Status    : Recorded                                                 │
└──────────────────────────────────────────────────────────────────────┘
```

> **Demo only:** Device names, mount paths, and timestamps are fictional.
