 Day 02: AWS EBS Storage & Disaster Recovery Restoration


Implement a block-level **Disaster Recovery (DR)** workflow using AWS EBS Volumes and Snapshots. The goal is to simulate data creation on a primary server, capture a point-in-time backup, restore it to a secondary server, and verify data integrity.



 Architecture & Implementation Steps

 Step 1: Primary Volume & Data Creation (Server-01)
 Created a **5 GiB gp3 EBS volume** in the same Availability Zone as `Server-01`.
 Attached the volume to `Server-01` as `/dev/sdb`.
 Formatted the volume with the `ext4` filesystem (`sudo mkfs -t ext4 /dev/nvme1n1`).
 Mounted the volume to `/mnt/data` and created a test file `test.txt` with verified data.

 Step 2: Backup Generation (EBS Snapshot)
 Unmounted the volume cleanly (`sudo umount /mnt/data`).
 Took a point-in-time **EBS Snapshot** named `Server-01-backup` via the AWS Console.

 Step 3: Disaster Recovery Restoration (Server-02)
 Created a new 5 GiB EBS volume directly from the snapshot.
 Attached the restored volume to `Server-02`.
 Repaired filesystem journals using Linux repair tools (`e2fsck -f -y /dev/nvme1n1`).
 Mounted the restored volume to `/mnt/restored-data`.



 Terminal Verification & Results

Below is the verified terminal output showing successful restoration of the mount path `/mnt/restored-data` and intact file contents (`Hello AWS Cloud, my data is safe!`):

<img width="539" height="190" alt="Image" src="https://github.com/user-attachments/assets/bd527ea1-4791-4845-b4dd-7751d90dd6a8" />


 Commands Summary
bash
File System Creation & Mount
sudo mkfs -t ext4 /dev/nvme1n1
sudo mkdir -p /mnt/data
sudo mount /dev/nvme1n1 /mnt/data

Repair & Recovery on Secondary Server
sudo e2fsck -f -y /dev/nvme1n1
sudo mount -t ext4 /dev/nvme1n1 /mnt/restored-data
cat /mnt/restored-data/test.txt
