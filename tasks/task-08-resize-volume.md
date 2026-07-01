# Task 08 - Resize and Extend a Volume

## Objective

Increase the size of an EBS volume and extend the Linux file system to use the new space.

---

## Scenario

The application data disk is almost full. You need to increase the EBS volume size without replacing the server.

---

## Steps

### 1. Modify the Volume in AWS

Console:

1. Go to **EC2**.
2. Choose **Volumes**.
3. Select `ebs-lab-data-volume`.
4. Choose **Actions**.
5. Choose **Modify volume**.
6. Change size from `8 GiB` to `12 GiB`.
7. Choose **Modify**.
8. Confirm the change.

### 2. Confirm New Disk Size on Linux

On the EC2 instance:

```bash
lsblk
df -h
```

The block device may show the new size before the file system does.

### 3. Extend the File System

For XFS directly on the device:

```bash
sudo xfs_growfs /data
```

For ext4 directly on the device:

```bash
sudo resize2fs /dev/nvme1n1
```

If your device uses a partition, grow the partition first:

```bash
sudo growpart /dev/nvme1n1 1
```

Then grow the file system.

---

## Verification

Run:

```bash
df -h /data
```

The `/data` file system should show the increased size.

---

## Important Note

EBS volume size can be increased, but it cannot be reduced directly. To move to a smaller volume, create a new smaller volume and copy the data.
