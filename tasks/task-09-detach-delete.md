# Task 09 - Detach and Delete a Volume

## Objective

Safely unmount, detach, and delete unused EBS volumes and snapshots to avoid unnecessary AWS charges.

---

## Scenario

The lab is complete. You need to clean up storage resources so the AWS account does not keep billing for unused volumes or snapshots.

---

## Steps

### 1. Unmount the Volume

On the EC2 instance:

```bash
sudo umount /data
```

If you mounted a restored volume:

```bash
sudo umount /restore
```

### 2. Remove fstab Entry

If you added `/data` to `/etc/fstab`, edit the file:

```bash
sudo nano /etc/fstab
```

Remove or comment out the `/data` line.

Test:

```bash
sudo mount -a
```

### 3. Detach the Volume

Console:

1. Go to **EC2**.
2. Choose **Volumes**.
3. Select the lab volume.
4. Choose **Actions**.
5. Choose **Detach volume**.
6. Confirm detach.

### 4. Delete the Volume

Console:

1. Wait until the volume state is `Available`.
2. Select the volume.
3. Choose **Actions**.
4. Choose **Delete volume**.
5. Confirm deletion.

### 5. Delete Snapshot if No Longer Needed

Console:

1. Go to **Snapshots**.
2. Select `ebs-lab-snapshot`.
3. Choose **Actions**.
4. Choose **Delete snapshot**.

---

## Verification

Confirm that:

- Lab volumes are deleted or no longer attached.
- Unneeded snapshots are deleted.
- The EC2 instance is stopped or terminated if you no longer need it.

---

## Final Cleanup Reminder

Check the EC2 dashboard for running instances, unattached volumes, elastic IP addresses, and snapshots.
