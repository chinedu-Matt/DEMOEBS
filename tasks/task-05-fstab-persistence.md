# Task 05 - Persist Mount with fstab

## Objective

Configure the EBS volume to mount automatically after the EC2 instance reboots.

---

## Scenario

The `/data` mount works now, but temporary mounts disappear after reboot. A production server needs storage mounts to persist. This step is done in the EC2 Instance Connect terminal because `/etc/fstab` is a Linux system file.

---

## Steps

### 1. Find the Volume UUID

Run:

```bash
sudo blkid
```

Find the UUID for the EBS device mounted at `/data`.

Example:

```text
UUID="abcd1234-5678-90ef-1234-567890abcdef" TYPE="xfs"
```

### 2. Back Up fstab

```bash
sudo cp /etc/fstab /etc/fstab.backup
```

### 3. Edit fstab

Open the file:

```bash
sudo nano /etc/fstab
```

Add a line like this:

```text
UUID=abcd1234-5678-90ef-1234-567890abcdef /data xfs defaults,nofail 0 2
```

Replace the UUID with your actual value.

### 4. Test the fstab Entry

Unmount and remount:

```bash
sudo umount /data
sudo mount -a
```

### 5. Confirm Mount

```bash
df -h
cat /data/test.txt
```

---

## Verification

The `/data` mount should return without errors after `sudo mount -a`.

Optional reboot test:

```bash
sudo reboot
```

After reconnecting, run:

```bash
df -h
```

The EBS volume should still be mounted on `/data`.

---

## Troubleshooting

If the instance fails to boot after editing `/etc/fstab`, detach the root volume and repair the file from another instance. Always keep a backup before editing.
