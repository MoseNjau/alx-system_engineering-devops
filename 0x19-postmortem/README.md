# Project Outage Postmortem

## Overview
This document provides a postmortem analysis of an outage that occurred during the release of ALX's System Engineering & DevOps project 0x19. The outage affected an isolated Ubuntu 14.04 container running an Apache web server, resulting in 500 Internal Server Errors for GET requests instead of the expected response, which was an HTML file defining a simple Holberton WordPress site.

## Issue Summary
- **Duration:** The outage occurred upon the release of the project at approximately 06:00 West African Time (WAT) and was resolved approximately 13 hours later at 19:20 Pacific Standard Time (PST).
- **Impact:** GET requests on the server led to 500 Internal Server Errors, affecting the availability of the WordPress site.
- **Root Cause:** The root cause of the outage was identified as a typo in the WordPress application code, specifically referencing an erroneous file extension ".phpp" instead of ".php".

## Timeline
- **06:00 WAT:** Outage detected upon project release.
- **19:20 PST:** Bug debugger (BDB) Brennan encounters the issue and begins debugging.
- **19:25 PST:** Checked running processes and examined Apache configuration.
- **19:30 PST:** Ran strace on Apache processes and identified the erroneous file extension.
- **19:45 PST:** Located and corrected the typo in the WordPress application code.
- **19:50 PST:** Tested server response and confirmed resolution.
- **19:55 PST:** Wrote a Puppet manifest to automate fixing similar errors in the future.

## Root Cause and Resolution
The root cause of the outage was a typo in the WordPress application code, specifically referencing an erroneous file extension ".phpp" instead of ".php". The issue was resolved by manually correcting the typo in the WordPress application code. Additionally, a Puppet manifest was created to automate the detection and correction of similar errors in the future.

## Corrective and Preventative Measures
To prevent similar outages in the future, the following measures are recommended:
1. **Testing:** Implement thorough testing procedures for the application before deployment to catch errors like typos early in the development process.
2. **Status Monitoring:** Enable uptime-monitoring services such as UptimeRobot to promptly alert administrators of any website outages.
3. **Automation:** Use automation tools like Puppet to automate error detection and correction processes, reducing the likelihood of similar issues occurring in the future.

By implementing these measures, we aim to minimize the risk of similar outages and ensure the stability and reliability of our web server and applications.

---

This document was generated based on a postmortem analysis of the outage. For further information or inquiries, please contact the project team.

