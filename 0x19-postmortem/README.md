Postmortem Report: E-Commerce Website Outage
Issue Summary

Duration of the Outage: June 15, 2024, 02:30 PM - 04:15 PM UTC
Impact: The e-commerce website experienced intermittent downtime during this period. Users encountered error pages when attempting to make purchases. Approximately 60% of users were affected, leading to significant revenue loss and customer frustration.
Root Cause: A misconfigured load balancer incorrectly routed traffic to a subset of backend servers, causing these servers to become overwhelmed and unresponsive.
Timeline
02:30 PM UTC - Issue Detected: Monitoring systems reported increased response times and error rates.
02:35 PM UTC - Detection Method: Automated monitoring alert triggered by increased 5xx error rates.
02:40 PM UTC - Initial Investigation: Engineers began investigating the load balancer configuration and server health. Assumptions were made that the issue might be related to server performance or an application bug.
03:00 PM UTC - Misleading Path: Investigation into server performance and application logs showed no anomalies, leading to incorrect assumptions that the issue might be with the database connectivity.
03:30 PM UTC - Escalation: The issue was escalated to the Infrastructure Team and senior system administrators.
03:45 PM UTC - Resolution: It was identified that the load balancer was routing all traffic to a specific set of backend servers due to a misconfigured health check setting. Reconfiguring the load balancer to properly distribute traffic across all available servers resolved the issue.
04:15 PM UTC - Incident Resolved: Full functionality was restored after reconfiguring the load balancer.
Root Cause and Resolution
Root Cause: The issue was caused by an incorrect health check configuration on the load balancer. The load balancer was set to route traffic only to servers that were not actually healthy, leading to a situation where only a few servers received all incoming traffic, which overwhelmed them and caused outages.
Resolution: The health check configuration on the load balancer was corrected to ensure proper distribution of traffic among all healthy servers. A thorough check was conducted to confirm that the traffic was being balanced correctly and that no additional issues were present.
Corrective and Preventative Measures
Improvements/Fixes:

Load Balancer Configuration: Review and update load balancer configuration practices to include thorough validation and testing before deployment.
Monitoring Enhancements: Enhance monitoring and alerting to include specific checks for load balancer configuration issues.
Incident Response Plan: Update the incident response plan to include detailed procedures for diagnosing and fixing load balancer-related issues.
Tasks to Address the Issue:

Task 1: Patch and update load balancer health check configuration to ensure proper traffic routing.
Task 2: Add specific monitoring and alerting for load balancer health checks to detect misconfigurations early.
Task 3: Review and test load balancer configurations regularly as part of the deployment process.
Task 4: Conduct a post-incident review and update documentation on troubleshooting load balancer issues.
Task 5: Implement a runbook for quick resolution of similar issues, including a checklist for validating load balancer configurations.
