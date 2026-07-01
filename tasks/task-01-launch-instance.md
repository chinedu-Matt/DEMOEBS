# Task 01 - Launch an EC2 Instance

## Objective

Launch a Linux EC2 instance that will be used to attach, mount, resize, and test EBS volumes.

---

## Scenario

You are preparing a test server for storage administration. Before creating and attaching extra EBS volumes, you need a running EC2 instance in a known Availability Zone.

---

## Steps

### 1. Open EC2

Console:

1. Sign in to the AWS Management Console.
2. Search for `EC2`.
3. Open the EC2 dashboard.
4. Select the region you want to use, for example `us-east-1`.

### 2. Launch Instance

Console:

1. Choose **Launch instance**.
2. Name the instance: `ebs-lab-instance`.
3. Select an AMI:
   - Amazon Linux 2023, or
   - Ubuntu Server LTS.
4. Select instance type: `t3.micro` or another free-tier eligible option.
5. Choose or create a key pair.
6. Allow SSH from your IP address.
7. Keep the default root volume.
8. Choose **Launch instance**.

### 3. Record Instance Details

Console:

1. Open the instance details page.
2. Record:
   - Instance ID
   - Public IPv4 address
   - Availability Zone, for example `us-east-1a`

---

## Verification

The instance should show `Running` in the EC2 console, and you should know its Availability Zone.

---

## Screenshot Suggestion

Save a screenshot of the running EC2 instance details page in the `screenshots/` folder.
