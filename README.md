# Brute-Force Detection

## Part 1: Create Alert Rule (Brute Force Attempt Detection)
Design a Sentinel Scheduled Query Rule within Log Analytics to detect when the same remote IP address has failed to log in to the same local host (Azure VM) 10 times or more within the last 5 hours:

![Brute Force Detection Rule](https://github.com/user-attachments/assets/2e4478e3-d35b-43f3-bc6b-3e72a43cae84)

![Query Configuration](https://github.com/user-attachments/assets/c1a1032e-bbdb-4155-8767-3e961508df46)

## Part 2: Trigger Alert to Create Incident
Once the alert rule detects a brute-force attempt, it triggers an incident in Microsoft Sentinel.

![Incident Trigger](https://github.com/user-attachments/assets/3194f3a3-794e-478b-937f-a55b261f81f5)

![Incident Details](https://github.com/user-attachments/assets/7229e254-4859-4e61-8383-61d147bb76b2)

## Part 3: Work Incident
Brute-force attempts potentially impacted more than 20 different virtual machines, originating from 15 different public IP addresses. The next step is to check whether any of these IP addresses successfully logged in.

No successful logins were found:

![No Results Found](https://github.com/user-attachments/assets/bb3371fa-9b73-426d-a272-f4bb529b1e93)

## Part 4: Post-Incident Response
The Network Security Group (NSG) was locked down to prevent RDP attempts from the public internet. A corporate policy was proposed to enforce this restriction on all VMs going forward using **Azure Policy**.
