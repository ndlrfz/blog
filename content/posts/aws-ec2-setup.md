+++
date = '2025-03-19T23:42:31+07:00'
draft = false
tags = ["aws"]
title = 'Create Amazon EC2 Instance'
+++

Guide to deploy Amazon EC2 instance with multiple AZ and installation script.

1. `EC2` -> `Launch Instance`
2. Enter instance name, select the operating system (AMI)
3. Select instance type (which server specs you need)
4. `Compare instance types` -> `Get advice` which will show you recommendation for your applications
5. Select key-pair SSH or generate new
6. Select **VPC** (for testing, use default. for production, always create custom VPC)
7. Select the subnet (YOU MUST CHEK THE AVAILABILITY ZONE HERE)
8. Security group to allow inbound traffic to specific port
9. `Advanced details` -> `User data` (enter your deployment script. Example: installing LAMP Stack, downloading source code, etc)
10. **Launch Instance**
