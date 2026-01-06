---

# AWS Cost Optimization Project – Orphan EBS Snapshot Cleanup using Lambda

## Overview

This project automates AWS cost optimization by identifying and deleting orphaned Amazon EBS snapshots using AWS Lambda. Orphaned snapshots are created when EC2 instances or EBS volumes are deleted but their snapshots are not removed, resulting in unnecessary storage costs.

The solution uses a serverless approach to periodically scan EBS snapshots and automatically clean up unused resources.

---

## Problem Statement

In many AWS environments:

* EC2 instances are created for workloads
* EBS snapshots are taken for backup purposes
* EC2 instances or volumes are deleted
* Snapshots are often forgotten and left behind

These unused snapshots continue to incur storage costs.

---

## Solution

An AWS Lambda function is implemented to:

* Retrieve all EBS snapshots in the account
* Check whether each snapshot is associated with any active EBS volume or EC2 instance
* Identify orphaned snapshots
* Automatically delete snapshots that are no longer in use

---

## Architecture

```
AWS Lambda
   ↓
EC2 & EBS APIs
   ↓
Identify Orphaned Snapshots
   ↓
Delete Unused Snapshots
   ↓
CloudWatch Logs
```

---

## Technologies Used

* AWS Lambda
* Amazon EC2
* Amazon EBS
* AWS IAM
* Amazon CloudWatch
* Python (Boto3)

---

## IAM Permissions

The Lambda execution role uses least-privilege permissions:

* ec2:DescribeSnapshots
* ec2:DescribeVolumes
* ec2:DescribeInstances
* ec2:DeleteSnapshot

---

## Execution

* The Lambda function can be executed manually from the AWS console
* It can also be scheduled using Amazon EventBridge for periodic cleanup

---

## Benefits

* Reduces unnecessary AWS storage costs
* Automates cloud resource cleanup
* Improves AWS account hygiene
* Serverless and scalable solution

---

## License

This project is for learning and demonstration purposes.

---

