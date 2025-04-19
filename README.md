# Bootcamp-SIEM-Project (Windows and Apache logs)

## Objective

This project was completed during my cybersecurity bootcamp to simulate a real-world SOC environment. I played the role of a Security Operations Center (SOC) analyst at a fictional company called Virtual Space Industries (VSI), which designs virtual-reality programs for businesses. My role involved designing a defensive monitoring solution and then testing its effectiveness when the environment was later attacked. I ingested and analyzed Windows Server and Apache Web Server logs in Splunk to detect potential attacks, built dashboards and alerts, and finally investigated simulated cyberattacks targeting these systems to determine what was compromised and how.

### Skills Learned

- Ingesting and analyzing logs in Splunk
- Creating reports and dashboards for real-time monitoring
- Writing threshold-based alerts
- Detecting patterns in attack data
- Performing comparative analysis between normal and attack logs
- Translating monitoring results into incident narratives for management

### Tools Used

- Splunk (running locally via Docker)
- Windows and Apache server logs (normal and attack datasets)
- SPL (Search Processing Language)
- Dashboard & visualization tools in Splunk UI

## Steps

### Day 1: Designing a Defensive Monitoring Solution

#### Log Ingestion
- Uploaded **Windows logs** and **Apache logs** into Splunk
- Labeled logs clearly with host values (`Windows_server_logs`, `Apache_logs`)

#### Report Creation
- Signature ID table
- Severity level breakdown
- Success vs failure login comparison
- HTTP methods
- Top 10 domains count of each HTTP response
- Count of each HTTP response

*Severity report from Windows Logs screenshot*
![image](https://github.com/user-attachments/assets/53dd9bf4-6513-458c-b61b-23b6f632bc34)

#### Alerts 
- Created baseline and the threshold alerts for:
  - VSI suspicious activity
  - Failed login attempts
  - High volume of successful logins
  - Account deletion (based on signature ID)
  - Non-US activity
  - HTTP POST

*Failed login threshold alert setup* 
![image](https://github.com/user-attachments/assets/ce5a7dbe-80b0-4bdd-8215-a3ab72ee6a9c)

#### Dashboards
- Windows Monitoring Dashboard
  - Signature trends over time
  - User activity analysis
  - Single-value gauges and charts
  
*Windows server monitoring dashboard*
![image](https://github.com/user-attachments/assets/a29964a4-8c36-4474-b93a-d1d5fed931a3)


- Apache Monitoring Dashboard
  - HTTP method time charts
  - Geographic clustering of IPs
  - Top referrers and user agents

*Apache web server monitoring dashboard*
![image](https://github.com/user-attachments/assets/8657f53d-daa5-4b95-b4bd-5122066a13c9)

---

### Day 2: Monitoring and Analyzing Simulated Attacks

#### New Log Ingestion
- Uploaded **Windows attack logs** and **Apache attack logs**

#### Analysis & Investigation
- Swapped log sources in reports, dashboards, and alerts:
  - From `windows_server_logs.csv` ➝ `windows_server_attack_logs.csv`
  - From `apache_logs.txt` ➝ `apache_attack_logs.txt`

#### Windows Attack Findings
- Spikes in failed logins, account password resets, and deleted accounts
- Suspiciously high number of successful logins from a single user
- Multiple signature IDs triggered over short time intervals
- Dashboard analysis findings: correlation between 'A user accout was locked out' matches suspicious activity with user_A.

*Line chart of user's activity during time of attack*
![image](https://github.com/user-attachments/assets/70aa09dd-f527-4d77-bcb9-48422a5e2358)


#### Apache Attack Findings
- High volume of HTTP GET and POST requests
- Unusual geographic traffic (international IPs) 
- Top URI hit suggested possible data exfiltration or brute-force probing

*Line chart analysis of GET and POST method activity during time of attack*
![image](https://github.com/user-attachments/assets/237df841-3e85-496a-8817-0f316b4793c1)


#### Adjusted Thresholds & Recommendations
- Reassessed alert thresholds based on post-attack metrics
- Identified dashboard panels that visualized incidents most clearly

#### Reflection
This project gave me great hands-on experience simulating the SOC analyst's possible work: designing a defesnive monitoring solution and investigating attack scenarios.  
