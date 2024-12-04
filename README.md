# Assignment-3 Part 2

## Introduction

In this assignment, you will:

Set up two Arch Linux servers.
Configure a load balancer to distribute traffic between the servers.
Deploy an updated generate_index script.
Add file server functionality to serve test files.


## Table of Contents

Task 1: Create Two Droplets

Task 2: Configure a Load Balancer

Task 3: Clone and Use Updated Script

Task 4: Configure the File Server


## Task 1: Create Two New DigitalOcean Droplets

Go to DigitalOcean's Control Panel.
Create Two Droplets:
Choose Arch Linux as the operating system.
Select the SFO3 region.
Apply the web tag to both droplets.
Configuration for basic, premium, etc,.
Setup Each Droplet:

Afer the droplets are set up it should look like this:

![droplets](images/droplets.png)


Connect via SSH to each droplet.
Install essential packages (nginx, ssh, etc.).
Set up your directory structure (/var/lib/webgen).

``` sudo mkdir -p /var/lib/webgen/{bin,documents,HTML} ```


## Task 2: Configure a Load Balancer

Create Load Balancer:
Go to the Networking > on the ledt side pane of the DigitalOcean control panel and select "Creat Loadbalancers" 
Create a new load balancer with these settings:
Region: SFO3 (same as droplets).
VPC: Default.
Tag: Use the "web" tag to balance traffic between your two droplets.
Type: External/Public.
Set up rules for HTTP traffic (port 80) and ensure SSL (optional).
You can rename it if you want

![lb](images/lb.png)


> Note: Make sure that when the loadbalancer is created it is correctly connected to both droplets and says Healthy

## Task 3:Clone Repository

Step 1: Clone the Updated Starter Code from the link

git clone https://git.sr.ht/~nathan_climbs/2420-as3-p2-start

Step 2: Move the generate_index Script
Move the generate_index script to the appropriate directory:

```
sudo mv 2420-as3-p2-start/generate_index /var/lib/webgen/bin/
```

Step 3: Grant Execute Permissions

Give the generate_index script executable permissions with this command:

```
sudo chmod +x /var/lib/webgen/bin/generate_index
```
Step 4: Create the documents Directory
Set up the directory for storing files using the command:


```
sudo mkdir -p /var/lib/webgen/documents
```

Step 5: Create Test Files in the documents Directory
Inside the documents directory, create two sample files:


```
sudo touch /var/lib/webgen/documents/file-one
```
```
sudo touch /var/lib/webgen/documents/file-two
```

Step 6: Create an index.html File
Generate a placeholder index.html file in the HTML directory:

```
sudo touch /var/lib/webgen/HTML/index.html
```

