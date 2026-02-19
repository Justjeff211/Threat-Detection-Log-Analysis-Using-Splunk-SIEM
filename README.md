# Threat Detection & Log Analysis Using Splunk SIEM

## Project Summary

This project simulates a real-world Tier 1 SOC analyst investigation using Splunk Enterprise (Free Tier).

Apache web server logs were ingested and analyzed using SPL (Search Processing Language) queries to identify suspicious activity patterns, including API targeting and HTTP method abuse.

The outcome includes detection queries, a formal incident report, and dashboard visualizations.

---

## Environment

- Platform: Splunk Enterprise 10.2.0 (Free Tier)
- Log Format: Apache `access_combined`
- Events Analyzed: 112 log entries
- Author: Mojalefa Lawrence Letsoara
- Level: Beginner / Entry-Level SOC

---

## Objectives

- Simulate SOC log ingestion workflow
- Develop SPL-based detections
- Identify suspicious HTTP behavior
- Perform statistical log analysis
- Produce formal incident documentation
- Build a SOC dashboard

---

## Key Findings

- 112 distinct IP addresses observed
- 14 HTTP 500 errors (12.5% of traffic)
- 4 successful DELETE (HTTP 200) requests
- 6 successful PUT (HTTP 200) requests
- `/api/users` identified as primary target
- Distributed traffic pattern suggests botnet-style behavior

---

## Recommended Mitigations

- Temporarily disable `/api/users` endpoint
- Block high-risk IP addresses at firewall level
- Disable HTTP DELETE and PUT methods unless required
- Implement rate limiting
- Deploy Web Application Firewall (WAF) protections

---

## SPL Query Examples

```spl
index=soc_log status=500
