# AWS Cloud Resume Project

## Overview

This personal project serves a dual purpose for me. It allows me to present my resume to employers in a more polished manner while also demostrating some cloud technologies.

## AWS Services Used

- **IAM:** Configured to enforce least privilege and uphold good security practices.
- **Route53:** Utilized to purchase the domain name and set up DNS records for routing.
- **S3 Bucket:** Employed to store HTML files for static website hosting.
- **AWS Certificate Manager (ACM):** Used for SSL certificate management.
- **CloudFront:** Utilized for content distribution and SSL encryption of online traffic. This ensures secure data transmission over the internet and may facilitate future use cases such as adding login/authentication functionality to the resume.

## Setup and Functionality

### 1. Setting up the Static Website on an S3 Bucket

Configuring static website hosting on the S3 bucket, defining a unique bucket name, and configuring public policies for the website to be publicly accessible were crucial steps for this task.
<img src="https://i.imgur.com/ijzAFIB.png" height="80%" width="80%" alt="Code commit permissions"/>
<br />
<br />

### 2. Purchasing the Domain Name and Configuring Routing with Route 53

I utilized Route 53 to register the domain name "iloricloud.com," allowing users to access my resume by simply typing "ilori.com" in their browsers. This setup enables traffic routing on the internet to my static S3 website.

### 3. Using AWS Certificate Manager (ACM) and CloudFront for SSL Encryption and Content Distribution

ACM was employed to request a certificate for my static website, ensuring authenticity and encrypting data in transit with SSL. Additionally, CloudFront was utilized for content distribution and HTTPS connections. It's worth noting that SSL certificates must be requested from the US-East-1 region for compatibility with major certificate distributors. Finally, I configured the SSL certificate with CloudFront to enable secure communication between users and the website.

### 4. Configuring CloudFront TTL to Check My S3 Cache and Update My Website When Changes Are Made to My S3 Bucket

One challenge I encountered was the delay in reflecting changes made to files in my S3 bucket on my CloudFront-distributed website. After manually versioning my files with /* a few times, I realized that this issue could be resolved through CloudFront configurations or a Lambda function triggered whenever changes were made to my S3 bucket, updating the cache on CloudFront accordingly. Instead of opting for a Lambda function, I chose to address the issue through CloudFront configurations.

I adjusted the Time to Live (TTL) settings to check my S3 cache for updates and distribute the most current S3 files every 1 minute, as opposed to every 1 day, which explained the delayed reflections of changes. While using /* for versioning works for automatic updates, configuring TTL is essential to determine how frequently cache hits or misses occur.
