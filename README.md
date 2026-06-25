# AWS EC2 EBS Backup and Restore Project

## Project Overview

This project demonstrates how to create, attach, mount, and manage Amazon Elastic Block Store (EBS) volumes with an Amazon EC2 instance. It also covers creating backups using EBS snapshots to ensure data durability and recovery.

## Architecture

Amazon EC2 Instance → Amazon EBS Volume → EBS Snapshot

## AWS Services Used

* Amazon EC2
* Amazon EBS (Elastic Block Store)
* EBS Snapshots
* Amazon Linux 2023

## Project Steps

### 1. Launched an Amazon EC2 Instance

* Created an EC2 instance using Amazon Linux 2023.
* Connected to the instance using EC2 Instance Connect.

### 2. Created an EBS Volume

* Created a new General Purpose SSD (gp3) EBS volume.
* Selected the same Availability Zone as the EC2 instance.

### 3. Attached the EBS Volume to EC2

* Attached the newly created EBS volume to the EC2 instance.

### 4. Verified the Attached Volume

Used the following command to verify the attached storage device:

```bash
lsblk
```

### 5. Formatted the EBS Volume

Created an XFS file system on the new volume:

```bash
sudo mkfs -t xfs /dev/nvme1n1
```

### 6. Mounted the Volume

Created a mount point and mounted the volume:

```bash
sudo mkdir /data
sudo mount /dev/nvme1n1 /data
```

### 7. Verified the Mount

```bash
df -h
```

### 8. Created Test Data

Created a sample file inside the mounted volume:

```bash
cd /data
sudo touch testfile.txt
ls
```

### 9. Configured Persistent Mounting

Retrieved the UUID:

```bash
sudo blkid
```

Configured automatic mounting by editing the `/etc/fstab` file.

```bash
sudo nano /etc/fstab
```

Added:

```bash
UUID=<volume-uuid> /data xfs defaults,nofail 0 2
```

Verified the configuration:

```bash
sudo mount -a
```

### 10. Created an EBS Snapshot

* Created a snapshot of the EBS volume from the AWS Management Console.
* Learned how snapshots can be used for backup and disaster recovery.

## Key Learnings

* Amazon EBS volume management
* Attaching and mounting EBS volumes
* Linux file system administration
* Persistent storage configuration using `/etc/fstab`
* EBS snapshots and backup strategies
* Data durability and disaster recovery concepts

## Project Outcome

Successfully created, attached, mounted, and configured an Amazon EBS volume with an EC2 instance. Implemented persistent storage and explored backup capabilities using EBS snapshots.

## Author

**Divya Vemulapalli**
