# License Usage Threshold Alert

### 🎯 Purpose

Detect when Splunk license usage is getting close to the daily quota.

---

### 🔧 SPL Query

```spl
index=_internal source=*license_usage.log type=RolloverSummary
| eval gb=round(b/1024/1024/1024,2)
| stats sum(gb) as used_gb by idx
```
### 🔔 Alert Condition

Trigger when:

```spl
used_gb > 70  (or whatever threshold is relevant)
```

### 📌 Why this alert matters

- Helps avoid license violations
- Useful for Ops and Support teams
- Early warning for noisy sources
