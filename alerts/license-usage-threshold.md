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
