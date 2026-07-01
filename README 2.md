## AWS EBS Volume Hands-On Lab


---

## Lab Overview

| # | Task | Difficulty |
|---|------|------------|
| 01 | [Launch an EC2 Instance](tasks/task-01-launch-instance.md) | Beginner |
| 02 | [Create an EBS Volume](tasks/task-02-create-volume.md) | Beginner |
| 03 | [Attach a Volume to an Instance](tasks/task-03-attach-volume.md) | Beginner |
| 04 | [Mount & Format the Volume on Linux](tasks/task-04-mount-format.md) | Intermediate |
| 05 | [Persist Mount with fstab](tasks/task-05-fstab-persistence.md) | Intermediate |
| 06 | [Create an EBS Snapshot](tasks/task-06-create-snapshot.md) | Intermediate |
| 07 | [Restore a Volume from Snapshot](tasks/task-07-restore-snapshot.md) | Intermediate |
| 08 | [Resize and Extend a Volume](tasks/task-08-resize-volume.md) | Advanced |
| 09 | [Detach and Delete a Volume](tasks/task-09-detach-delete.md) | Advanced |

---

## Repo Structure

```text
aws-ebs-lab/
├── screenshots/        # Console screenshots for each task
├── scripts/            # Reserved for future helper scripts
├── tasks/              # Step-by-step markdown for each task
└── README.md
```

---

## Tools Used

- AWS Management Console
- Amazon EC2
- Amazon Elastic Block Store
- Amazon Linux 2023 or Ubuntu Server
- EC2 Instance Connect terminal
- Region: `us-east-1`
- Instance type: `t3.micro` or free-tier eligible equivalent

---

## Key Concepts Covered

- EC2 instance preparation for EBS labs
- EBS volume creation and Availability Zone matching
- Attaching and detaching EBS volumes
- Linux block device discovery with `lsblk`
- Formatting volumes with `mkfs`
- Mounting volumes temporarily and permanently
- Persisting mounts using `/etc/fstab`
- Creating and restoring EBS snapshots
- Modifying EBS volume size
- Extending partitions and file systems
- Cleaning up AWS resources to avoid unwanted charges

---

## Console vs Terminal Work

Most tasks are completed in the AWS Management Console. Tasks 04 and 05 require the EC2 Instance Connect terminal because EBS can only be created and attached from AWS; formatting, mounting, and `/etc/fstab` persistence happen inside the Linux operating system.

---

## Important Notes

- EBS volumes must be in the same Availability Zone as the EC2 instance they attach to.
- Deleting an EC2 instance does not always delete separately created EBS volumes.
- Always check for unused volumes and snapshots after completing the lab.
- Use a test environment only. Do not perform these tasks on production volumes.

---

## Author

**chinedu-Matt**  
B.Sc. Computer Science (NOUN) | DevOps & Cloud Engineering Learner
