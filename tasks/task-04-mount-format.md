# Task 04 - Mount & Format the Volume on Linux

## Objective

Format the attached EBS volume with a file system and mount it on the Linux instance.

---

## Scenario

The EBS volume is attached from the AWS Console, but Linux cannot store files on it until it has a file system and a mount point. This task is done in the EC2 Instance Connect terminal because it is operating system work, not AWS Console work.

---

## Steps

### 1. Connect to the Instance

Console:

1. Go to **EC2**.
2. Choose **Instances**.
3. Select `ebs-lab-instance`.
4. Choose **Connect**.
5. Choose **EC2 Instance Connect**.
6. Choose **Connect**.

### 2. Identify the New Disk

Run:

```bash
lsblk
```

Look for the newly attached disk. On Nitro-based EC2 instances, it commonly appears as:

- `/dev/nvme1n1`

On some instances, it may appear as `/dev/xvdf`.

### 3. Create a File System

For an unformatted test volume, run:

```bash
sudo mkfs -t xfs /dev/nvme1n1
```

If your device is named differently, replace `/dev/nvme1n1` with the correct device name from `lsblk`.

### 4. Create a Mount Point

```bash
sudo mkdir /data
```

### 5. Mount the Volume

```bash
sudo mount /dev/nvme1n1 /data
```

### 6. Test File Creation

```bash
echo "EBS lab test file" | sudo tee /data/test.txt
cat /data/test.txt
```

---

## Verification

Run:

```bash
df -h
lsblk
```

The new EBS volume should be mounted on `/data`.

---

## Important Note

Formatting a disk deletes existing data on that disk. Only run `mkfs` on a new lab volume.
