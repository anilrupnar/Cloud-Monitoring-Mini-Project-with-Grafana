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

### 1. **Create a Virtual Machine**:
   - **Instance Name**: Server
   - **Amazon Server Image**: Ubuntu Server 24.04 LTS (HVM), SSD Volume Type (Free tier).
   - **Instance Type**: t2.micro
   - **Key Pair**: Create a new key pair (e.g., `project_access_key`).
   - **Network Settings**: Create a new security group (e.g., `Demoproject`).
   - **Security Group Permissions**:
     
     ![AWS Security Group](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/aws%20security%20group.jpg)
    
   - **Storage**: 25GB
    
     ![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/Aws.jpg)
    
   - Launch the instance.

### 2. **Connect to the EC2 Instance**:
   - Download [MobaXterm](https://mobaxterm.mobatek.net/download.html) to connect to the EC2 instance.
   - Use the EC2 instance's public IP address and add the public key (e.g., `project_access_key`).
   - Update the Ubuntu machine:
     ```bash
     sudo apt-get update
     ```

### 3. **Install Grafana**:

#### Step 1: Install Dependencies

Ensure that your system has the required dependencies by running the following command:

```bash
sudo apt-get install -y software-properties-common

### Step 2: Add Grafana APT Repository
To enable the official Grafana repository, use the following command:

```bash
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"

### Step 3: Install Grafana GPG Key
Next, download and add the Grafana GPG key to authenticate the packages:

```bash
sudo wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -

### Step 4: Update Repository and Install Grafana
After adding the repository, update your package list and install Grafana:

```bash
sudo apt-get update
sudo apt-get install grafana
