+++
date = '2025-03-21T00:22:46+07:00'
draft = false
tags = ["aws"]
title = 'Guide to AWS VPC Peering'
+++

## Intro

VPC Peering is needed when you want to connect **two** different VPC each other. Mostly used for cross-department in SDLC.

In this example, I will connect between two VPCs _Developer_ and _Finance_, and each VPC attached to different EC2 intance.

## Check Private IP range of an EC2 instance

**Make sure to check local IP address range for both _Developer_ and _Finance_ instances.**

1. Navigate to the _Developer_ instance, select and click on the `Subnet ID`
2. In the subnet section, select your subnet name and click on the `Route table`
3. In the route table section, select your route table and click `Routes` tab
4. Take a notes on the private IP address range for the _Developer_ instance

## Creating VPC Peering

1. Go to the `VPC` menu via console, select `Peering connections`, then click `Create peering connection` button
2. Enter your peering details such as:
   * _Name_: Developer <> Finance
   * _VPC ID (Requester)_: Select the **Developer** VPC and check the local IP address range of the VPC
   * _VPC ID (Accepter)_: Select the **Finance** VPC and check the local IP range of the VPC
   * _Tags_: Name => Developer <> Finance
3. Confirm click the `Create peering connection`
4. On the peering details, you can see the **Status** is _Pending_
5. Click `Actions` menu and select `Accept request` and confirm again (The **Status** of peering become _Active_)

## Adding VPC Peering to Subnet Route Table

**This must be done on EC2 servers for both _Developer_ and _Finance_.**

**Here I will configure the _Developer_ instance.**

1. Back to the EC2 instance and select _Developer_ instance details, then `Subnet ID => Route table => Routes` (like the first step)
2. Click `Edit routes` to add new routes for VPC peering
3. Click `Add route` with the following:
   * _Destination_: Enter local IP address range for the _Finance_ instance
   * _Target_: **Peering connection** and select your _VPC Peering_ that you've created
   * **Save changes**

4. Now move to the EC2 instance and select the _Finance_ instance. Then, do the same as on top, but make sure to enter the _IP address range_ of the _Developer_ instance in the _Destination_.

## Allow ICMP/Ping between EC2 Instances

In this example, I will allow ping to the _Finance_ instance from the _Developer_ instance.

1. Click on the EC2 and select the _Finance_ instance
2. Click on the `Security` tab and then click `Security groups` section
3. In the `Inbound rules` tab, click `Edit inbound rules`
4. Now `Add rule`
   * _Type_: Custom ICMP- IPv4
   * _Source_: Enter the range IP address of _Developer_ instance
   * **Save rules**

## Test VPC Peering

1. Connect to your EC2 instance (_Developer_) via _Session Manager_ or _SSH_
2. You can now ping to the local IP of the _Finance_ instance
