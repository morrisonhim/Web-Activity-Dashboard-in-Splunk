# Splunk Web Activity Monitoring Dashboard
This project walks through creating a Splunk dashboard to analyze web server activity using apache_mixed_access_full.json logs. The dashboard covers time-based filtering, key web activity summaries, error statistics, URI insights, top users, and geographic traffic visualization.

## 🧪 Lab Setup
**Environment**
+ Splunk Enterprise / Splunk Free (installed locally)
+ Sample Dataset: apache_mixed_access_full (1).json
+ Host: DESKTOP-DK91R5E
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

**Task 2: Web Activities**
Goal: Provide a quick overview of general web activity using Single Value panels.
1. Total Web Requests
+ Panel type: Single value
+ Title: Total Web Requests
+ Search query: source="apache_mixed_access_full (1).json" host="DESKTOP-DK91R5E" sourcetype="_json"
| stats count AS "Total Web Requests"
![total web request](https://github.com/morrisonhim/Web-Activity-Dashboard-in-Splunk/blob/main/total%20web%20request.png)

2. Successful Responses
+ Panel Type: Single Value
+ Title: Successful Response
+ Search Query: source="apache_mixed_access_full (1).json" host="DESKTOP-DK91R5E" sourcetype="_json" method=GET status=200
| stats count AS "Successful Responses"
![successful responses](https://github.com/morrisonhim/Web-Activity-Dashboard-in-Splunk/blob/main/successful%20responses.png)

3. Client Errors
+ Panel Type: Single Value
+ Title: Client Errors
+ Search Query: source="apache_logs.json" host="DESKTOP-DK91R5E" sourcetype="_json" | where status>500 | stats count AS "Client Errors"
![clent errors](https://github.com/morrisonhim/Web-Activity-Dashboard-in-Splunk/blob/main/client%20errors.png)

4. Server Errors 
+ Panel Type: Single Value
+ Title: Server Errors 
+ Search Query:source="apache_logs.json" host="DESKTOP-DK91R5E" sourcetype="_json" | where status>500 | stats count AS "Server Errors"
![server errors](https://github.com/morrisonhim/Web-Activity-Dashboard-in-Splunk/blob/main/server%20errors.png)

**Task 3: Web Stats**
Goal: Give a quick summary of Web Statstics.
1. Top Requested URIs
+ Click on Add Panel
+ Under New, choose Bar Chart
+ Use Shared Time Picker time_range
+ Set Content Title to "Top Requested URIs"
+ Enter the Search String: source="apache_mixed_access_full (1).json" host="DESKTOP-DK91R5E" sourcetype="_json" 
| stats count AS "Hits" by uri
![top uris](https://github.com/morrisonhim/Web-Activity-Dashboard-in-Splunk/blob/main/top%20uris.png)

2. Top Users by IP Address
+ Click on Add Panel
+ Under New, choose Bar Chart
+ Use Shared Time Picker time_range
+ Set Content Title to "Top Users by IP Address"
+ Enter the Search String: source="apache_mixed_access_full (1).json" host="DESKTOP-DK91R5E" sourcetype="_json" 
| stats count AS IP by ip
![]

