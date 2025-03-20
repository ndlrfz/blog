+++
date = '2025-03-20T08:30:32+07:00'
draft = false
title = 'Amazon EC2 Basic: Connect and Change Instance Type'
+++

## How to connect to Amazon EC2 instance

1. Using `Session Manager` via AWS console
2. Using `SSH` command, key SSH is needed to secure authentication
3. Using IAM policies that control SSH access to instances

## How to Increase Specs of Amazon EC2

1. Stop the instance first (after instance stopped, both IP and and DNS gone)
2. Select instance > `Actions` > `Instance Settings`
   * _Change auto recovery behavior_: changing how instance auto-recovery
   * _Change instance type_: change or upgrade instance type
   * _Change CPU options_: change the current CPU spec
   * _Edit user data_: modify current user data
3. Start again the instance
