# Sudden Drop in Ingestion Alert

### 🎯 Purpose

Detect when a source drastically reduces the number of logs being ingested.

---

### 🔧 SPL Query

```spl
index=your_index
| bin _time span=5m
| stats count as event_count by _time
| eventstats median(event_count) as baseline
| where event_count < baseline * 0.5
```

### 🔔 Alert Condition

Trigger when:

``` event_count drops 50% or more below baseline ```


### 📌 Why this alert matters

- Detects ingestion pipeline disruptions
- Identifies broken forwarders early
- Helps avoid monitoring blind spots
