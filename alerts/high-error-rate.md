# High Error Rate Alert

### 🎯 Purpose
Detect when the application experiences an unusually high number of HTTP 5xx errors within a short window.

---

### 🔧 SPL Query
```spl
index=your_index sourcetype=your_sourcetype status>=500 status<600
| timechart span=5m count as error_count 
```
🔔 Alert Condition

Trigger when:

``` error_count > 50 ```

📌 Why this alert matters

- Identifies backend issues early
- Helps reduce downtime
- Useful for Ops, Dev, SRE teams

