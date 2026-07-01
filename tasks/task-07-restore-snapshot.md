# Task 07 - Restore a Volume from Snapshot

## Objective

Restore data by creating a new EBS volume from a snapshot.

---

## Scenario

A storage volume was lost or needs to be cloned. You will use a snapshot to create a replacement volume and confirm the data is available.

---

## Steps

### 1. Create Volume from Snapshot

Console:

1. Go to **EC2**.
2. Choose **Snapshots**.
3. Select `ebs-lab-snapshot`.
4. Choose **Actions**.
5. Choose **Create volume from snapshot**.
6. Set Availability Zone to the same AZ as `ebs-lab-instance`.
7. Add tag:
   - Key: `Name`
   - Value: `ebs-lab-restored-volume`
8. Choose **Create volume**.

### 2. Attach Restored Volume

Console:

1. Go to **Volumes**.
2. Select `ebs-lab-restored-volume`.
3. Choose **Actions**.
4. Choose **Attach volume**.
5. Select `ebs-lab-instance`.
6. Device name: `/dev/sdg`.
7. Choose **Attach volume**.

### 3. Mount Restored Volume

On the EC2 instance:

```bash
lsblk
sudo mkdir /restore
sudo mount /dev/xvdg /restore
```

If the restored device has a different name, use the correct one from `lsblk`.

### 4. Check Restored Data

```bash
ls -l /restore
cat /restore/test.txt
```

---

## Verification

The restored volume should contain the same test file created before the snapshot.

---

## Cleanup for This Task

Unmount the restored volume if you no longer need it:

```bash
sudo umount /restore
```
