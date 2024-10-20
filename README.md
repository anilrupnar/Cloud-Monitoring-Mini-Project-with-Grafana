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
```

#### Step 2: Add Grafana APT Repository

To enable the official Grafana repository, use the following command:

```bash
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"

```

#### Step 3: Install Grafana GPG Key

Next, download and add the Grafana GPG key to authenticate the packages:

```bash
sudo wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```

#### Step 4: Update Repository and Install Grafana
After adding the repository, update your package list and install Grafana:

```bash
sudo apt-get update
sudo apt-get install grafana
```

#### Step 5: Start and Enable Grafana Service

Start the Grafana server and enable it to run at startup:

```bash
sudo /bin/systemctl start grafana-server
```
#### Step 6: Access Grafana
Once Grafana is running, you can access the Grafana web interface by navigating to:

```bash

http://localhost:3000
(ex.http://52.70.170.54:3000/)
```
#### The default login credentials are:

- Username: admin
- Password: admin

 ![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/5.png)

  
#### Change New Password 

 ![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/6.png)

### 4.Genrate Github Personal Token

## Generate a GitHub Personal Access Token (PAT) Steps :

Follow these steps to generate a GitHub Personal Access Token (PAT) that you can use for authenticating with GitHub APIs, pushing/pulling code, and managing repositories:

### Step 1: Log in to GitHub
- Go to [GitHub](https://github.com) and log in with your account credentials.

### Step 2: Go to Developer Settings
- In the top-right corner of any GitHub page, click on your profile picture.
- Select **Settings** from the dropdown.
- Scroll down on the left sidebar and click **Developer settings**.

### Step 3: Navigate to Personal Access Tokens
- Under **Developer settings**, click on **Personal access tokens**.
- Choose **Tokens (classic)** for general access, or **Fine-grained tokens** for more granular control (currently in beta).

### Step 4: Generate New Token
- Click the **Generate new token** button.

### Step 5: Configure the Token
- **Note**: Provide a meaningful description for your token (e.g., "Access to XYZ repository").
- **Expiration**: Optionally set an expiration date (7 days, 30 days, 60 days, 90 days, or no expiration).

### Step 6: Set Scopes and Permissions
Select the appropriate scopes accourding to Project need like this :

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/1.png)

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/2.png)

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/3.png)


### Step 7: Generate Token
- Scroll down and click the **Generate token** button.
- GitHub will display the token **once**, so make sure to **copy** it immediately.

### Step 8: Save the Token
- **Store the token** securely in a password manager or any secure location. You **cannot** view this token again once you leave the page.


