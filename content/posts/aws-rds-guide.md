+++
date = '2025-03-21T21:30:12+07:00'
draft = false
tags = ["aws"]
title = 'Guide to Amazon RDS (Relational Datbase Service)'
+++

## Intro

In short, RDS or Relational Database Service is a datbase server managed by AWS in the cloud. RDS offers both open source (MySQL, MariaDB, PostgreSQL) and commercial database server (Oracle Datbase, SQL Server) as a service.

By default, RDS will set up automatic backup and database snapshot.

You can also deploy RDS in multiple AZ, which provides high-availability for your database. In multiple AZ deployment, RDS will automatically sync replicates to a standby RDS instance in different AZ.

You can also create _read-only_ replica of RDS for ready-heavy database workloads.

## Provision Amazon RDS

1. In the AWS console, type `database` and select `Aurora and RDS`
2. Select the `Databases` menu and click `Create database`
3. Select the `Standard create` method, especially for customizing your database configurations
4. Select your database engine, for example `MariaDB`
5. Select the `Engine version` for your database
6. Select the template that yiu want to use:
   * Production
   * Dev/Test
   * Free Tier
7. enter your RDS name in the `DB instance identifier`
8. For the credentials settings:
   * _Master username_: enter or leave it as edefault `admin`
   * _Credentials Management_: use `Self managed` for testing only
   * _Master password_: Enter your password and repeat
9. Move to the `Instance configurations`
   * Select **Burstable classes**
   * Select the instance type for your RDS
   * For storage type `gp3` and allocate the storage to `20 GB`
10. For the `VPC` and `DB Subnet`, you can use default or custom isolated VPC
11. **Public access** to _no_ and **VPC Security Group** to _Choose existing_
12. On the `Additional storage configuration`

* **Check** the _Enable storage autoscaling_

13. On the `Availability and durability`, select the `Create standby instance` option
14. **Disable** the `Performance Insight` and `Enhanced Monitoring`
15. In the `Additional configuration`, configure the following

* _Initial database name_: You must enter the database name for your application. RDS does not create database by default
* _DB parameter group_ and _option group_: You can leave it as default

16. Check the `Enable automatic backup` and select the `Backup interval`
17. Check the `Enable enryption` to enable encryption of your database at rest
18. In the `Maintenance` section

* **Uncheck** the `Enable auto minor update`
* Select **No preference** on the `Maintenance window`

19. Review the cost for your database monthly and click `Create database`

The database instance will be created within **5-10 minutes**. Make sure to click the `reload` button to check the status until `Available`.

## Create Read-Replicate in Amazon RDS

1. From your console, go to the `Aurora and RDS` section, then click `Databases`
2. Click your database instance to get details
3. Within your database instance details, click `Action` and select `Create read replica`
4. Select your main RDS that you want to create as replica and configure details as on top

The read-replica will be created within 5-10 minutes.

## Migrate with DMS (Database Migration Service)

You can also migrate your database to AWS RDS via DMS or Database Migration Service.
