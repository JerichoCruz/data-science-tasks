<h1>Failed Remote Desktop Protocol (RDP) with IP Geolocation Information</h1>

<h2>Description</h2>
<b>The <a href="https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1">Powershell script</a> in this repository is responsible for parsing out Windows Event Log information for failed RDP attacks and using a third party API to collect geographic information about the attackers location.
</b>
<br />
<br />
The script is used in this lab where I setup Microsoft Sentinel (SIEM) and connect it to a live virtual machine acting as a honey pot for 24 hours. I take it a step further and load the custom logs into Power BI to create my own Security Information and Event Management (SIEM). We will observe live attacks (RDP Brute Force) from all around the world. I will use a custom PowerShell script to look up the attackers Geolocation information and plot it on PowerBI!
<br />
<br />

<p align="center">
<img src="https://jerichocruz.com/images/sentinel/eventviewer-geo.png" height="85%" width="85%" alt="RDP event fail logs to IP Geographic information"/>
</p>

<h2>Cloud Services Used</h2>

- <b>Microsoft Sentinel</b> is a cloud-native security information and event manager (SIEM) platform that uses built-in AI to help analyze large volumes of data across an enterprise. 
- <b>Log Analytics Workspace</b> is a unique environment for log data from Azure Monitor and other Azure services, such as Microsoft Sentinel and Microsoft Defender for Cloud. Each workspace has its own data repository and configuration but might combine data from multiple services.
- <b>Virtual Machines</b> is an on-demand, scalable computer resource that is available in Azure. 
- <b>Microsoft Defender for Cloud</b> is a Cloud Security Posture Management (CSPM) and Cloud Workload Protection Platform (CWPP) for all of Azure, on-premises, and multicloud (Amazon AWS and Google GCP) resources.

<h2>Languages Used</h2>

- <b>PowerShell:</b> Extract RDP failed logon logs from Windows Event Viewer
- <b>Power Query Formula Language (M Language):</b> Load custom logs into Power BI

<h2>Programs Used</h2>

- <b>Microsoft Power BI</b> is an interactive data visualization software product developed by Microsoft

<h2>Utilities Used</h2>

- <b>ipgeolocation.io:</b> IP Address to Geolocation API

<h2>Steps</h2>

1. Create Windows 10 Virtual Machine on Azure
2. Allow all in Firewall
3. Create Log Analytics Workspace (LAW)
4. Enable gathering VM logs in Microsoft Defender for Cloud
5. Connect Log Analytics to VM
6. Setup Microsoft Sentinel
7. Log into VM with Remote Desktop (Fail 1 logon for Event Viewer)
8. Observe Event Viewer Logs in VM
9.  Turn off Windows Firewall on VM
10. Download PowerShell Script
11. Get Geolocation.io API Key
12. Run Script To get Geo Data from attackers
13. Create custom log in LAW to bring in our custom log
14. Create custom fields/extract fields from raw custom log data
15. Setup Power BI environment
16. Load into Power BI using Power Query Script
17. Setup map in Power BI with Latitude and Longitude (or country)
18. Periodic refresh on Power BI

<h2>Attacks from Thailand coming in; Custom logs being output with geodata</h2>

<p align="center">
<img src="https://jerichocruz.com/images/sentinel/law-honeypot1-logs.png" height="85%" width="85%" alt="Honeypot Logs"/>
</p>

<h2>Dashboard of incoming attacks after 24 hours (built custom logs including geodata)</h2>

<p align="center">
<img src="https://jerichocruz.com/images/sentinel/rdpbruteforcedash.gif" height="85%" width="85%" alt="Power BI Dashboard"/>
</p>

<h2>Key Takeaways</h2>

- As soon as anything gets put on the internet, people are going to try to get into it. They don't care if you're a big business or an individual.
- You are a target of opportunity to everyone
- Try to avoid common usernames: administrator, admin, user, etc
  - Disable if possible
- Use multifactor authentication! If MFA is not available, use strong passwords/passphrases

<h2>Acknowledgements</h2>

- <a href="https://github.com/joshmadakor1">Josh Makador</a> for his amazing tutorials and tech tips. Check him out for similar projects!


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
