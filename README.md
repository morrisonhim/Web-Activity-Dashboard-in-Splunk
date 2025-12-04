# Splunk Web Activity Monitoring Dashboard
This project walks through creating a Splunk dashboard to analyze web server activity using apache_mixed_access_full.json logs. The dashboard covers time-based filtering, key web activity summaries, error statistics, URI insights, top users, and geographic traffic visualization.

## 🧪 Lab Setup
**Environment**
+ Splunk Enterprise / Splunk Free (installed locally)
+ Sample Dataset: apache_mixed_access_full (1).json
+ Host: webserver
+ Sourcetype: _json

**Setup Steps**
+ Launch Splunk and upload your JSON Apache log file
+ Navigate to Dashboards → Create New Dashboard
+ Name your dashboard (e.g., Web Activity Monitoring)
+ Begin adding inputs and panels as outlined below

**Task 1: Setting Up Time Range Input**
To ensure consistency across all dashboard panels:
+ Click Add Input
+ Select Time
+ Click the pencil icon
+ Set:
  - Label: Time Range
  - Token: time_range
  - Add another input:
  - Select Submit
- Note: For all future panels, set the time to the shared token time_range

**Task 1: Web Activities**
Goal: Provide a quick overview of general web activity using Single Value panels.
1. Total Web Requests
+ Panel type: Single value
+ Title: Total Web Requests
+ Search query: source= "apache_mixed_access_full (1).json" host="webserver" sourcetype="_json"
| stats count AS "Total Web Requests"
