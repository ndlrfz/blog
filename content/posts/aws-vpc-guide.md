+++
date = '2025-03-20T18:37:15+07:00'
draft = false
title = 'Guide to AWS VPC (Virtual Private Cloud)'
+++

## Intro

VPC or Virtual Private Cloud is an isolated internal network on AWS environment. When creating Amazon EC2, the default VPC will be created and attached to the instance.

For production, you must create custom VPC and do not use the default.

To access VPC, you can use the AWS console. Or, you can access through the EC2 instance detail, in the `Subnet ID` section.

## Allow HTTP Access to EC2 Instance

1. Select your EC2 instnace, move to details, click `Subnet ID`.
2. Select your subnet and click `Route Table` tab (Route Table define rules of your network traffic from your subnet or gateway is directed)
3. Click your Route Table name to get the details
4. Selecy your routable name, and move to the `Route` tab, click `Edit Route`
5. Click `Add Route` to allow internet to access your instance via gateway
   * _Destination_: 0.0.0.0/0
   * _Target_: Internet Gateway
   * Choose your internet gateway
   * **Save changes**

## Open HTTP in Security Group

6. Move to the EC2 instance menu and select your instance
7. Select the `Security` tab and click your `Security Group`
8. Select `Inbound Rules` and click `Edit Inbound Rules` > `Add Rule`
   * _Type_: HTTP
   * _Source_: Anywhere IPv4

## Allow Access to anywhere from EC2 via Security group

9. On the `Security group` of your instance, select the `Outbound Rules`
10. Click `Edit outbound rules`

* _Type_: All traffic
* _Destination type_: Custom
* _Destination_: 0.0.0.0/0
