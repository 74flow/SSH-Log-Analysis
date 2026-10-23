# SSH Log Analysis and Brute-Force Detection with Splunk

## Overview

This project analyzes SSH authentication logs using Splunk to identify suspicious login activity, potential brute-force attacks, and unauthenticated connections.

## Objectives

- Identify successful and failed SSH login attempts.
- Identify source IP addresses generating repeated authentication failures.
- Detect potential brute-force and password-spraying activity.
- Track successful SSH logins by source IP and destination host.
- Monitor connections that occur without authentication.
- Configure Splunk alerts and dashboards for security monitoring.

## Tools and Technologies

- Splunk Enterprise or Splunk Free
- Search Processing Language (SPL)
- JSON authentication logs
- Git and GitHub

## Project Structure

- `sample-data/ssh_log.json` — sanitized sample SSH log events.
- `splunk/queries.spl` — SPL searches for security monitoring.
- `splunk/field-extractions.conf` — example field extraction configuration.
- `splunk/alert-configuration.md` — alert setup and detection logic.
- `splunk/dashboard.xml` — dashboard configuration, if exported.
- `screenshots/` — evidence of searches, visualizations, and alerts.

## Detection Use Cases

1. Successful SSH logins
2. Failed SSH login attempts
3. Multiple failed authentication attempts
4. Connections without authentication
5. Potential brute-force activity exceeding five attempts within ten minutes

## Validation

Validate the ingested data using:

```spl
index=ssh_logs
| stats count by event_type
```

Confirm that the expected event types and fields are extracted correctly before running detection searches.

## Visualizations

- Bar chart: Top 10 source IPs by failed login count.
- Dashboard panel: Successful SSH logins by source and destination.
- Timechart: Unauthenticated SSH connections over time.

## Security Considerations

Only use authorized and sanitized log data. This project is intended for defensive security monitoring and incident investigation.

## Project Status

In progress — detection searches, field validation, alert configuration, and dashboard development will be documented as each task is completed.
