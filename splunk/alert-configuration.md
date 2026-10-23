index=ssh_logs auth_success=false
| bin _time span=10m
| stats count AS failed_events
        sum(auth_attempts) AS total_attempts
        by _time id.orig_h id.resp_h
| where total_attempts > 5 OR failed_events > 5
| sort - total_attempts
