+++
date = '2025-03-19T22:42:45+07:00'
draft = false
tags = ["aws"]
title = 'Static Hosting with Amazon S3'
+++

Here step-by-step to set up static hosting with Amazon S3:

1. Go to **S3** and select your bucket name
2. Upload your HTML files
3. Click **Permission** tab and **turn off** the **Block all public access**. To use S3 as static web hosting, you must turn off this
4. Move to the **Bucket Policy** and review your current policy. Make sure only **s3:GetObject** policy is enabled
5. Move to the **Default encryption** and make sure the default **server side encryption** is enabled
6. Scroll down to the **Static website hosting** and click **Edit**
   * *static web hoosting*: **Enable**
   * *Hosting type*: **Host static website**
   * *index_document*: **index.html** (make sure it i uploaded)
