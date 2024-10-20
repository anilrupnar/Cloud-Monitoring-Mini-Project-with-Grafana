# Cloud Monitoring Mini Project with Grafana

## Project Overview

This project demonstrates how to monitor GitHub and GitLab repositories using Grafana. It provides insights into repository activity, including commits, pull requests, and issues, helping teams better manage their projects.


## Features

- Monitor GitHub and GitLab repositories.
- Visualize metrics such as commits, pull requests, and issues.
- Customizable dashboards to focus on specific metrics.
- Real-time data updates for ongoing project management.

## Technologies Used

- **Grafana**: For visualizing repository metrics.
- **GitHub/GitLab**: Source code management platforms.
- **Cloud Provider**: (AWS) for hosting the virtual machine.

## Setup Instructions

1. **Create a Virtual Machine**:
   - Launch a T2 medium instance on your preferred cloud provider.
   - Ensure that port 3000 is open in your security group.
   ![Logo](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/Aws.jpg)

2. **Connect to the VM**:
   - Use SSH to connect to your instance.

3. **Install Grafana**:
   ```bash
   sudo apt update
   # Follow installation steps based on your OS (download, install, and start Grafana)



   ubuntu@ip-172-31-44-6:~$ sudo dpkg -i grafana-enterprise_11.2.2+security~01_amd64.deb
(Reading database ... 77870 files and directories currently installed.)
Preparing to unpack grafana-enterprise_11.2.2+security~01_amd64.deb ...
Unpacking grafana-enterprise (11.2.2-01) over (11.2.2-01) ...
dpkg: dependency problems prevent configuration of grafana-enterprise:
 grafana-enterprise depends on musl; however:
  Package musl is not installed.

dpkg: error processing package grafana-enterprise (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grafana-enterprise
ubuntu@ip-172-31-44-6:~$ sudo apt-get update
sudo apt-get install musl
Hit:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu noble-security InRelease
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  musl
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 416 kB of archives.
After this operation, 804 kB of additional disk space will be used.
Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu noble/universe amd64 musl amd64 1.2.4-2 [416 kB]
Fetched 416 kB in 0s (5061 kB/s)
Selecting previously unselected package musl:amd64.
(Reading database ... 77870 files and directories currently installed.)
Preparing to unpack .../musl_1.2.4-2_amd64.deb ...
Unpacking musl:amd64 (1.2.4-2) ...
Setting up musl:amd64 (1.2.4-2) ...
Setting up grafana-enterprise (11.2.2-01) ...
info: Selecting UID from range 100 to 999 ...

info: Adding system user `grafana' (UID 111) ...
info: Adding new user `grafana' (UID 111) with group `grafana' ...
info: Not creating home directory `/usr/share/grafana'.
### NOT starting on installation, please execute the following statements to configure grafana to start automatically using systemd
 sudo /bin/systemctl daemon-reload
 sudo /bin/systemctl enable grafana-server
### You can start grafana-server by executing
 sudo /bin/systemctl start grafana-server
Processing triggers for man-db (2.12.0-4build2) ...
needrestart is being skipped since dpkg has failed
ubuntu@ip-172-31-44-6:~$  sudo /bin/systemctl daemon-reload
 sudo /bin/systemctl enable grafana-server
Synchronizing state of grafana-server.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable grafana-server
Created symlink /etc/systemd/system/multi-user.target.wants/grafana-server.service → /usr/lib/systemd/system/grafana-server.service.
ubuntu@ip-172-31-44-6:~$  sudo /bin/systemctl start grafana-server
ubuntu@ip-172-31-44-6:~$

