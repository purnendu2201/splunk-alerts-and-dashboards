# No Logs From Source Alert

### 🎯 Purpose

Detect when a critical source stops sending logs in Splunk.

---

### 🔧 SPL Query
```spl
index=your_index sourcetype=your_sourcetype
| stats max(_time) as last_event
```

🔔 Alert Condition

Trigger when:

```now() - last_event > 900   (15 minutes)```

📌 Why this alert matters
- Helps find ingestion breakages early
- Ideal for forwarder monitoring
  
