# Task 06 - Create an EBS Snapshot

## Objective

Create a snapshot backup of the EBS volume.

---

## Scenario

Before making storage changes, you need a backup. EBS snapshots provide point-in-time backups that can be used to restore volumes later.

---

## Steps

### 1. Prepare the Volume

On the EC2 instance, make sure data exists:

```bash
ls -l /data
cat /data/test.txt
```

For a cleaner backup, flush file system buffers:

```bash
sync
```

### 2. Create Snapshot

Console:

1. Go to **EC2**.
2. Choose **Volumes**.
3. Select `ebs-lab-data-volume`.
4. Choose **Actions**.
5. Choose **Create snapshot**.
6. Description: `Snapshot of ebs-lab-data-volume`.
7. Add tag:
   - Key: `Name`
   - Value: `ebs-lab-snapshot`
8. Choose **Create snapshot**.

---

## Verification

Go to **Snapshots** and confirm the snapshot status changes to `Completed`.

---

## Screenshot Suggestion

Save a screenshot of the completed snapshot.
