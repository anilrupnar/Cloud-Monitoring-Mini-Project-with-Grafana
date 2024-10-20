# Cloud Monitoring Mini Project with Grafana

## Project Overview

This project demonstrates how to monitor GitHub and GitLab repositories using Grafana. It provides insights into repository activity, including commits, pull requests, and issues, helping teams better manage their projects.

# Table of Contents

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Setup Instructions](#setup-instructions)
   - [1. Create a Virtual Machine](#1-create-a-virtual-machine)
   - [2. Connect to the EC2 Instance](#2-connect-to-the-ec2-instance)
   - [3. Install Grafana](#3-install-grafana)
     - [Step 1: Install Dependencies](#step-1-install-dependencies)
     - [Step 2: Add Grafana APT Repository](#step-2-add-grafana-apt-repository)
     - [Step 3: Install Grafana GPG Key](#step-3-install-grafana-gpg-key)
     - [Step 4: Update Repository and Install Grafana](#step-4-update-repository-and-install-grafana)
     - [Step 5: Start and Enable Grafana Service](#step-5-start-and-enable-grafana-service)
     - [Step 6: Access Grafana](#step-6-access-grafana)
5. [Generate a GitHub Personal Access Token (PAT)](#4-generate-a-github-personal-access-token-pat)
6. [Install GitHub Data Source in Grafana](#5-install-github-data-source-in-grafana)
7. [6. Create a New Grafana Dashboard](#6-create-a-new-grafana-dashboard)
5. [Final Output](#7-final-output)
6. [Contact Information](#contact-information)

---


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

### 4.Generate a GitHub Personal Access Token (PAT) Steps

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


### 5. Install GitHub Data Source in Grafana

#### Step 1: Navigate to Connections and Select Data Sources

Go to the **Connections** section in Grafana and click on **Data Sources**.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/7.png)

#### Step 2: Install GitHub Data Source Plugin

Search for the GitHub data source plugin in the plugin list and install it.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/10.png)

#### Step 3: Configure the GitHub Data Source Plugin with a Personal Access Token

After installing the GitHub data source plugin, select it from the list. Then, configure it by providing a GitHub Personal Access Token (PAT) to allow Grafana to access GitHub repository data.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/11.png)

#### Step 4: Click Save & Test

Once the GitHub data source is configured with the access token, click **Save & Test** to verify the connection.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/12.png)


### 6. Create a New Grafana Dashboard 

#### Step 1: Search for a GitLab Data Source Dashboard Template

Go to Google and search for:

   `gitlab data source grafana dashboard`

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/13.png)

#### Step 2: Copy the Dashboard Template Code 

You can use a pre-built Grafana dashboard for the GitLab data source to visualize GitLab metrics. Check out the dashboard here:

[GitLab Data Source Grafana Dashboard link](https://grafana.com/grafana/dashboards/3749-gitlab/)

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/21.png)

#### Step 3: Import the Dashboard Template into Grafana 

In Grafana, go to the **Import** section and paste the dashboard template code.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/15.png)

#### Step 4: Insert the Copied Dashboard Template Code 

Paste the copied dashboard template code and click **Load**.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/16.png)

#### Step 5: Name the Grafana Dashboard and Add GitHub Data Source 

Give the Grafana dashboard a name and select the **GitHub data source** option that you previously configured.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/18.png)

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/17.png)

#### Step 6: Customize the Organization and Repository

Change the organization (your GitHub username), choose the repository you want to analyze, and set the branch to **main**. See the image below for guidance.

![AWS Storage](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/19.png)



### 7. Final Output 

After setting up the GitHub or GitLab data source and configuring the dashboard, you should see the visualized metrics as shown below.

![Final Output Example 1](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/19.png)

![Final Output Example 2](https://github.com/anil-rupnar/Cloud-Monitoring-Mini-Project-with-Grafana/blob/main/images/20.png)

---

Thank you for reading my README file!

Feel free to connect with me:

- **LinkedIn**: [Anil Rupnar](https://www.linkedin.com/in/anil-rupnar/)
- **Email**: anilrupnar2003@gmail.com

