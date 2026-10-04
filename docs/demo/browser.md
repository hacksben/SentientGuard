# 🌐 Browser Monitoring — Demo

> **SENTINEL PoC · Fictional browser activity** + **This also theft password which which web i login**

```text
┌──────────────────────────────────────────────────────────────────────┐
│                     SENTINEL :: BROWSER                              │
├──────────────────────────────────────────────────────────────────────┤
│ STATUS      ● MONITORING                                             │
│ BROWSERS    Firefox · Chrome · Brave                                │
│ EVENTS      6                                                        │
└──────────────────────────────────────────────────────────────────────┘

 BROWSER ACTIVITY
 ─────────────────────────────────────────────────────────────────────

 TIME       BROWSER    EVENT          DOMAIN
 ─────────────────────────────────────────────────────────────────────
 14:22:17   Firefox    PAGE VISIT     example.com
 14:23:01   Firefox    SEARCH         search.example
 14:23:41   Chrome     PAGE VISIT     docs.example
 14:24:08   Brave      PAGE VISIT     security.example
 14:24:52   Chrome     SEARCH         search.example
 14:25:10   Brave      PAGE VISIT     developer.example
```

### Terminal View

```text
$ sentinel browser --today

14:22:17  Firefox  VISIT   example.com
14:23:01  Firefox  SEARCH  search.example
14:23:41  Chrome   VISIT   docs.example
14:24:08  Brave    VISIT   security.example
14:24:52  Chrome   SEARCH  search.example
14:25:10  Brave    VISIT   developer.example

6 browser events recorded.
```

### Security Timeline

```text
14:22:17 ── Browser activity
14:23:01 ── Search activity
14:23:41 ── Browser activity
14:24:08 ── Browser activity
14:24:52 ── Search activity
14:25:10 ── Browser activity
```

> **Privacy:** This demonstration uses fictional domains and contains no real browsing history or search queries.
