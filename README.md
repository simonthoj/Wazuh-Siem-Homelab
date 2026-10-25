# Wazuh-Siem-Homelab

**Overview**
This project documents my hands-on deployment of a Security Information and Event Management (SIEM) lab using Wazuh. The lab uses an Ubuntu Server virtual machine to host the Wazuh platform and a Windows endpoint to generate security telemetry.

The goal is to develop practical skills in SIEM administration, endpoint monitoring, security event analysis, and troubleshooting.

**Objectives**
Deploy an all-in-one Wazuh server.
Configure network connectivity and remote Linux administration.
Enroll a Windows endpoint as a Wazuh agent.
Explore security alerts and endpoint telemetry.
Configure and test File Integrity Monitoring (FIM).
Document troubleshooting and investigation findings.

**Lab Architecture**
Hypervisor: Oracle VirtualBox
SIEM server: Ubuntu Server 24.04 LTS
SIEM platform: Wazuh 4.x
Endpoint: Windows
Remote administration: SSH from Windows PowerShell
Networking: Bridged adapter on a private LAN

**Implementation**
1. Ubuntu Server Deployment
Installed Ubuntu Server 24.04 LTS in VirtualBox and configured bridged networking to allow the VM to communicate with the Windows host.

2. Remote Administration
Enabled SSH on Ubuntu Server and established remote administration through Windows PowerShell.

3. Wazuh Installation
Deployed the Wazuh server, indexer, and dashboard on a single Ubuntu virtual machine using the Wazuh installation assistant.

4. Windows Agent Enrollment
Installed the Wazuh agent on the Windows endpoint, configured it to communicate with the Wazuh server, and verified that the agent reached the Active state in the dashboard.

5. File Integrity Monitoring
Located the Windows agent configuration file (ossec.conf) and began configuring monitored directories.

The next validation step is to generate controlled file changes and confirm that Wazuh records the corresponding events.

**Virtual Disk Capacity**

Problem: The initial Wazuh installation failed because the virtual disk ran out of space.

Resolution: Increased the virtual disk capacity and expanded the Ubuntu logical volume and ext4 filesystem. Verified the available capacity using df -h.

Lesson learned: Virtual disk capacity, partition size, logical volume allocation, and filesystem size are separate layers that may require separate adjustments.

**Operating System Compatibility**

Problem: The initial installer warned that the operating system was not in its recommended list.

Resolution: Rebuilt the lab using Ubuntu Server 24.04 LTS before completing the deployment.

Lesson learned: Verify operating system compatibility with the vendor's installation documentation before deploying security infrastructure.

**Windows Agent Connectivity**

Problem: The Windows agent initially appeared as Pending in the Wazuh dashboard.

Resolution: Checked the agent service and network connectivity, then verified that the agent became Active.

Lesson learned: Agent enrollment, service status, and network connectivity are important troubleshooting checkpoints.

**Skills Demonstrated**

Linux system administration
Virtual machine configuration
TCP/IP networking
SSH remote administration
SIEM deployment and administration
Endpoint agent enrollment
Basic security monitoring
Technical troubleshooting
Security documentation

**Future Improvements**

Configure and validate File Integrity Monitoring.
Investigate Windows authentication events and failed logins.
Document security alerts and map relevant detections to MITRE ATT&CK.
Add a Linux endpoint and compare telemetry across operating systems.
Explore vulnerability detection and security configuration assessment.
