+++
date = '2025-03-20T08:48:35+07:00'
draft = false
tags = ["aws"]
title = 'Guide to AWS Calculator'
+++

1. Visit [https://calculator.aws](https://calculator.aws) and click `Create Estimate`
2. In the breadcamp menu, click `My Estimate`
3. `Create group` - You can set up price based on software stack or deployment types (prod/stag/dev) and assign each as a group
   * Enter group name
   * Confirm
4. Within your group, click `Add service` - AWS calculator provides more than 175 AWS services
5. Select your region and _find your service_, for example **EC2**, then `Configure`
6. Enter details your estimation for EC2 usage:
   * Description
   * Region
   * _Tenancey_: shared (default) or dedicated server (more expensive)
   * _Operatin System_: Linxu Windows etc
   * _Workloads_: select the usage as needed for your organization
      * Contant usage
      * Daily spike traffic
      * Weekly spike traffic
      * Monthly spike traffic
   * _Baseline_: number of EC2 that will be running
   * _Peak_: max number of EC2 that running during **peak** time
   * _Duration of peak_: duration of peak (based on your monitoring to ensure hours and time)
7. On the `EC2 Instances`, select the instance family, vCPUs, memory, and network performance
   * Select the right instance as needed for your workloads (IMPORTANT)
8. On the `Payment` section, choose **On-demand**, which means you pay for compute capacity by the hour or second with _no long-term commitments_
   * Other option, you can select _Saving plans_ options. TYhere is _discounts_, but you need to commit at least _1 or 3-years_.
   * Or you can choose _other purchasing options_
      * _Standard Reserverd Instances_: higher discount, but allow modifications only within the same family. You can upgrade _t2_ to _t3_ and you cannot upgrade _t3_ to _mx_
      * _Convertible Reserved Instances_: lower discount, but flexible on modifications, cross instance types, tenancy, and operating systems
9. To check estimated workloads per hour, click on the link _estimated workload hours_
10. Add the Amazon EBS (Elastic Block Storage) for your EC2

   ```txt
   * _Storage type_: **general purpose SSD (gp3)**
   * _general purpose_: **IOPS** (inputs/outputs) _30_
   * _Storage amout_: **10 GB**
   * _Snapshot frquency_: **weekly**
   ```

11. For the `Inbound Data transfer`, select `Internet (free)` with amount `1` `TB per month`
12. For the `Outbound Data Transfer`, select `Internet` with the amount `100` `GB per month`
13. You can review the data transfer cost voa _show calculations_
14. **Save and add service** or you can _view summary_
15. If you need supports from Amazon supports, click **Add support**
16. Click **Share** to create public link for your estimation
