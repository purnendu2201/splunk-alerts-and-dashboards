# HTTP 5xx Spike Detection

### 🎯 Purpose

Detect sudden spikes in backend/API/server errors.

---

### 🔧 SPL Query

```spl
index=your_index status>=500 status<600
| timechart span=5m count as errors
| eventstats avg(errors) as avg_errors
| where errors > avg_errors * 2
```

### 🔔 Alert Condition

Triggered when:

```spl 
errors > 2 × average baseline
```

### 📌 Why this alert matters

- Detects backend failures
- Helps identify code issues or outages
