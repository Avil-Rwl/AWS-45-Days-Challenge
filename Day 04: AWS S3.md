 Day 04: AWS S3 (Simple Storage Service)
 
 Overview
Amazon S3 is an object storage service offering industry-leading scalability, data availability, security, and performance. Today's lab focused on hosting a static website, configuring bucket policies, versioning, data lifecycle management, and understanding hybrid storage migration with AWS Snow Family & Storage Gateway.


 1. S3 Core Fundamentals
   Buckets & Objects: Buckets are globally unique containers; objects are individual files stored with key-value metadata.

S3 Versioning: Keeps multiple variants of an object in the same bucket to protect against accidental overwrites or deletions.

Public Access & Bucket Policies: Resource-based JSON policies that manage granular permissions (e.g., granting public read access for web hosting).

2. S3 Storage Classes & Lifecycle Rules

S3 Standard: High availability, low latency for active data.

3 Glacier / Deep Archive: Low-cost storage for long-term backups (retrieval times range from minutes to hours).

  Lifecycle Rules: Automated transitions of objects between storage classes (or deletion) based on age to optimize costs.

3. Data Migration & Hybrid Storage
 AWS Snow Family (Offline Transport)
 
  Snowcone:Ultra-portable (8 TB–14 TB) for edge computing/remote locations.

  Snowball Edge: Storage-optimized (~80 TB) & Compute-optimized devices for petabyte-scale data migration.

  Snowmobile:45-foot ruggedized shipping container capable of moving up to 100 PB.
  AWS Storage Gateway (Hybrid Cloud):

  File Gateway:Exposes S3 objects as NFS/SMB file shares.

  Volume Gateway: Provides block storage volumes (iSCSI) backed by EBS snapshots in S3 (Cached & Stored modes).

  Tape Gateway: Replaces physical magnetic tape infrastructure with virtual tapes in S3 Glacier.

 Hands-On Lab: Static Website Hosting

1. Bucket Creation:** Created globally unique bucket `aws-45day-challenge-s3-demo`.
2. Versioning: Enabled versioning under bucket properties.
3. Public Access: Unchecked *Block all public access*.
4. Bucket Policy: Applied JSON policy for public object read permissions:
   json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::aws-s3-avii-123/*"
       }
     ]
   }
