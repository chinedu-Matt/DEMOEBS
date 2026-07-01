# Task 03 - Attach a Volume to an Instance

## Objective

Attach the new EBS volume to the EC2 instance so the operating system can use it.

---

## Scenario

The storage volume has been provisioned. Now it must be attached to the application server before it can be formatted and mounted.

---

## Steps

### 1. Select the Volume

Console:

1. Go to **EC2**.
2. Choose **Volumes**.
3. Select `ebs-lab-data-volume`.
4. Choose **Actions**.
5. Choose **Attach volume**.

### 2. Attach to Instance

Console:

1. Instance: select `ebs-lab-instance`.
2. Device name: use `/dev/sdf`.
3. Choose **Attach volume**.

---

## Verification

The volume state should change from `Available` to `In-use`.

On the instance, run:

```bash
lsblk
```

You should see a new disk, commonly shown as `xvdf` or `nvme1n1`, depending on the instance type and operating system.

---

## Screenshot Suggestion

Save a screenshot of the attached volume showing the instance ID.
