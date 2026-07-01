# Task 02 - Create an EBS Volume

## Objective

Create a new EBS volume that can later be attached to the EC2 instance.

---

## Scenario

Your application server needs an additional disk for application data. You will create a separate EBS volume instead of using the root disk.

---

## Steps

### 1. Open Volumes

Console:

1. Go to **EC2**.
2. In the left navigation, choose **Elastic Block Store**.
3. Choose **Volumes**.
4. Choose **Create volume**.

### 2. Configure the Volume

Console:

1. Volume type: `gp3`.
2. Size: `8 GiB`.
3. Availability Zone: select the same Availability Zone as your EC2 instance.
4. Add a tag:
   - Key: `Name`
   - Value: `ebs-lab-data-volume`
5. Choose **Create volume**.

---

## Verification

The new volume should show:

- State: `Available`
- Size: `8 GiB`
- Type: `gp3`
- Availability Zone matching your EC2 instance

---

## Screenshot Suggestion

Save a screenshot showing the newly created EBS volume.
