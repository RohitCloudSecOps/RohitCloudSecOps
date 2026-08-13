# AWS EFS Multi-AZ Shared File System Lab

## 1. Lab Objective

The objective of this lab is to create an AWS Elastic File System (EFS) and mount the same shared file system across three EC2 instances located in three different Availability Zones.

### Architecture

```text
                         AWS Region
                         us-east-2
                              |
          +-------------------+-------------------+
          |                   |                   |
       AZ 2a               AZ 2b               AZ 2c
          |                   |                   |
   +--------------+    +--------------+    +--------------+
   | Test1-2a     |    | Test1-2b     |    | Test1-2c     |
   | EC2 Instance |    | EC2 Instance |    | EC2 Instance |
   +--------------+    +--------------+    +--------------+
          |                   |                   |
          |                   |                   |
          +-------------------+-------------------+
                              |
                       +-------------+
                       | Test_EFS    |
                       | Amazon EFS  |
                       +-------------+
                              |
                     Shared File Storage
```

### EC2 Instances

| Instance | Availability Zone | Mount Directory |
| -------- | ----------------- | --------------- |
| Test1-2a | us-east-2a        | `/Test1_EFS`    |
| Test1-2b | us-east-2b        | `/Test2_EFS`    |
| Test1-2c | us-east-2c        | `/Test3_EFS`    |

### EFS File System

**EFS Name:** `Test_EFS`

**EFS File System ID:**

```text
fs-00908b3ec43df8b56
```

**EFS DNS Name:**

```text
fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com
```

---

# 2. Prerequisites

The following resources are required:

* AWS account
* Three EC2 instances
* Instances located in different Availability Zones
* One Amazon EFS filesystem
* EFS mount targets
* Common/custom security group
* NFS access on TCP port `2049`
* Internet/NAT access where required for package installation
* SSH access to EC2 instances

---

# 3. EC2 Instance Configuration

Three EC2 instances were created in the `us-east-2` region.

### Instance 1

```text
Instance Name: Test1-2a
Availability Zone: us-east-2a
Mount Point: /Test1_EFS
```

### Instance 2

```text
Instance Name: Test1-2b
Availability Zone: us-east-2b
Mount Point: /Test2_EFS
```

### Instance 3

```text
Instance Name: Test1-2c
Availability Zone: us-east-2c
Mount Point: /Test3_EFS
```

The purpose of placing the EC2 instances in different Availability Zones is to demonstrate that the same EFS filesystem can be accessed from multiple AZs.

---

# 4. Create Amazon EFS

An Amazon EFS filesystem was created with the following configuration.

```text
File System Name: Test_EFS
File System ID: fs-00908b3ec43df8b56
Region: us-east-2
```

The EFS filesystem provides shared network-based storage that can be mounted by multiple EC2 instances simultaneously.

---

# 5. EFS Mount Targets

EFS mount targets should be available in the required Availability Zones.

Expected configuration:

```text
us-east-2a → EFS Mount Target
us-east-2b → EFS Mount Target
us-east-2c → EFS Mount Target
```

This allows EC2 instances in each Availability Zone to connect to EFS through the appropriate network path.

---

# 6. Security Group Configuration

A common custom security group was configured for the EFS connectivity.

The most important inbound rule is:

```text
Protocol: TCP
Port: 2049
Service: NFS
Source: EC2/EFS Security Group
```

### NFS Port

```text
TCP 2049
```

Port `2049` is required because Amazon EFS uses the NFS protocol for mounting and accessing the filesystem.

### Recommended Security Group Relationship

```text
EC2 Security Group
        |
        | TCP 2049
        ↓
EFS Security Group
```

Using the EC2 security group as the source is preferable to opening NFS to the entire internet.

---

# 7. Install NFS Client

The NFS client package must be installed on each EC2 instance.

## Amazon Linux / RHEL-based systems

Run:

```bash
sudo yum install -y nfs-utils
```

For newer systems where `dnf` is used:

```bash
sudo dnf install -y nfs-utils
```

## Ubuntu/Debian-based systems

Run:

```bash
sudo apt update
sudo apt install -y nfs-common
```

The installation should be performed on:

```text
Test1-2a
Test1-2b
Test1-2c
```

---

# 8. Verify NFS Installation

Verify that the NFS client is available.

```bash
mount.nfs4 -V
```

or:

```bash
rpm -qa | grep nfs
```

For Ubuntu:

```bash
dpkg -l | grep nfs
```

---

# 9. Create EFS Mount Directory – Instance 1

Connect to:

```text
Test1-2a
```

Create the mount directory:

```bash
sudo mkdir -p /Test1_EFS
```

Verify:

```bash
ls -ld /Test1_EFS
```

Expected result:

```text
/Test1_EFS
```

---

# 10. Mount EFS on Test1-2a

Use the EFS NFS mount command:

```bash
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com:/ /Test1_EFS
```

### Important

The mount command must include the destination directory.

The complete command is:

```bash
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com:/ /Test1_EFS
```

---

# 11. Verify EFS Mount – Test1-2a

Run:

```bash
df -h
```

Look for the EFS filesystem.

You can also run:

```bash
mount | grep nfs
```

or:

```bash
mount | grep efs
```

Another useful command:

```bash
df -Th /Test1_EFS
```

The output should show that `/Test1_EFS` is backed by the EFS filesystem.

---

# 12. Create EFS Mount Directory – Instance 2

Connect to:

```text
Test1-2b
```

Create:

```bash
sudo mkdir -p /Test2_EFS
```

Verify:

```bash
ls -ld /Test2_EFS
```

---

# 13. Mount EFS on Test1-2b

Run:

```bash
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com:/ /Test2_EFS
```

Verify:

```bash
df -Th /Test2_EFS
```

Also:

```bash
mount | grep efs
```

---

# 14. Create EFS Mount Directory – Instance 3

Connect to:

```text
Test1-2c
```

Create:

```bash
sudo mkdir -p /Test3_EFS
```

Verify:

```bash
ls -ld /Test3_EFS
```

---

# 15. Mount EFS on Test1-2c

Run:

```bash
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com:/ /Test3_EFS
```

Verify:

```bash
df -Th /Test3_EFS
```

Also:

```bash
mount | grep efs
```

---

# 16. Final Mount Architecture

At this stage, the same EFS filesystem is mounted on all three EC2 instances.

```text
                    Test_EFS
                       |
          fs-00908b3ec43df8b56
                       |
       +---------------+---------------+
       |               |               |
       ↓               ↓               ↓
    Test1-2a        Test1-2b        Test1-2c
    us-east-2a      us-east-2b      us-east-2c
       |               |               |
       ↓               ↓               ↓
 /Test1_EFS        /Test2_EFS        /Test3_EFS
```

The three directories are different local mount-point names, but they point to the same EFS filesystem.

---

# 17. Create Files from Instance 1

Connect to:

```text
Test1-2a
```

Change to the EFS mount:

```bash
cd /Test1_EFS
```

Create the first file:

```bash
sudo touch RohitApps.txt
```

Create the second file:

```bash
sudo touch RohitTools.txt
```

Verify:

```bash
ls -l /Test1_EFS
```

Expected files:

```text
RohitApps.txt
RohitTools.txt
```

---

# 18. Add Data to Instance 1 Files

To demonstrate actual file content:

```bash
echo "Application information created from Test1-2a" | sudo tee /Test1_EFS/RohitApps.txt
```

And:

```bash
echo "Tools information created from Test1-2a" | sudo tee /Test1_EFS/RohitTools.txt
```

Verify:

```bash
cat /Test1_EFS/RohitApps.txt
```

```bash
cat /Test1_EFS/RohitTools.txt
```

---

# 19. Verify Instance 1 Files from Instance 2

Connect to:

```text
Test1-2b
```

Run:

```bash
ls -l /Test2_EFS
```

Because `/Test2_EFS` is connected to the same EFS filesystem, the following files should be visible:

```text
RohitApps.txt
RohitTools.txt
```

Verify:

```bash
cat /Test2_EFS/RohitApps.txt
```

```bash
cat /Test2_EFS/RohitTools.txt
```

This demonstrates that the files created on `Test1-2a` are accessible from `Test1-2b`.

---

# 20. Create File from Instance 2

On:

```text
Test1-2b
```

Create:

```bash
sudo touch /Test2_EFS/RohitDocs.conf
```

Add sample content:

```bash
echo "Documentation configuration created from Test1-2b" | sudo tee /Test2_EFS/RohitDocs.conf
```

Verify:

```bash
ls -l /Test2_EFS
```

---

# 21. Verify Instance 2 File from Instance 1

Go back to:

```text
Test1-2a
```

Run:

```bash
ls -l /Test1_EFS
```

You should now see:

```text
RohitApps.txt
RohitTools.txt
RohitDocs.conf
```

Verify:

```bash
cat /Test1_EFS/RohitDocs.conf
```

This confirms two-way shared access through EFS.

---

# 22. Create Files from Instance 3

Connect to:

```text
Test1-2c
```

Create:

```bash
sudo touch /Test3_EFS/RohitPowerbi.conf
```

Create:

```bash
sudo touch /Test3_EFS/RohitTech.txt
```

Add sample content:

```bash
echo "Power BI configuration created from Test1-2c" | sudo tee /Test3_EFS/RohitPowerbi.conf
```

```bash
echo "Technology information created from Test1-2c" | sudo tee /Test3_EFS/RohitTech.txt
```

Verify:

```bash
ls -l /Test3_EFS
```

Expected files:

```text
RohitApps.txt
RohitTools.txt
RohitDocs.conf
RohitPowerbi.conf
RohitTech.txt
```

---

# 23. Final Cross-AZ Verification

The most important part of this lab is proving that the same EFS filesystem is accessible from all three Availability Zones.

## From Test1-2a

Run:

```bash
ls -l /Test1_EFS
```

Expected:

```text
RohitApps.txt
RohitTools.txt
RohitDocs.conf
RohitPowerbi.conf
RohitTech.txt
```

## From Test1-2b

Run:

```bash
ls -l /Test2_EFS
```

Expected:

```text
RohitApps.txt
RohitTools.txt
RohitDocs.conf
RohitPowerbi.conf
RohitTech.txt
```

## From Test1-2c

Run:

```bash
ls -l /Test3_EFS
```

Expected:

```text
RohitApps.txt
RohitTools.txt
RohitDocs.conf
RohitPowerbi.conf
RohitTech.txt
```

---

# 24. Final File Layout

All three instances should ultimately see the same shared files.

```text
EFS: Test_EFS
|
+-- RohitApps.txt
+-- RohitTools.txt
+-- RohitDocs.conf
+-- RohitPowerbi.conf
+-- RohitTech.txt
```

The only difference is the local mount directory used by each EC2 instance.

```text
Test1-2a
└── /Test1_EFS
    ├── RohitApps.txt
    ├── RohitTools.txt
    ├── RohitDocs.conf
    ├── RohitPowerbi.conf
    └── RohitTech.txt

Test1-2b
└── /Test2_EFS
    ├── RohitApps.txt
    ├── RohitTools.txt
    ├── RohitDocs.conf
    ├── RohitPowerbi.conf
    └── RohitTech.txt

Test1-2c
└── /Test3_EFS
    ├── RohitApps.txt
    ├── RohitTools.txt
    ├── RohitDocs.conf
    ├── RohitPowerbi.conf
    └── RohitTech.txt
```

---

# 25. Test File Modification

To demonstrate that the shared filesystem is not only readable but also writable, modify a file from one instance.

On `Test1-2c`:

```bash
echo "Updated from Test1-2c" | sudo tee -a /Test3_EFS/RohitTech.txt
```

Then on `Test1-2a`:

```bash
cat /Test1_EFS/RohitTech.txt
```

The modification should be visible.

This demonstrates shared read/write access.

---

# 26. Test File Creation from All Availability Zones

A complete test matrix can be used.

| Test   | Source Instance | File                | Verification        |
| ------ | --------------- | ------------------- | ------------------- |
| Test 1 | Test1-2a        | `RohitApps.txt`     | Test1-2b / Test1-2c |
| Test 2 | Test1-2a        | `RohitTools.txt`    | Test1-2b / Test1-2c |
| Test 3 | Test1-2b        | `RohitDocs.conf`    | Test1-2a / Test1-2c |
| Test 4 | Test1-2c        | `RohitPowerbi.conf` | Test1-2a / Test1-2b |
| Test 5 | Test1-2c        | `RohitTech.txt`     | Test1-2a / Test1-2b |

---

# 27. Useful Troubleshooting Commands

## Check mounted filesystems

```bash
df -h
```

## Check filesystem type

```bash
df -Th
```

## Check EFS/NFS mount

```bash
mount | grep efs
```

or:

```bash
mount | grep nfs
```

## Check mount directory

```bash
ls -la /Test1_EFS
```

```bash
ls -la /Test2_EFS
```

```bash
ls -la /Test3_EFS
```

## Check network connectivity to EFS

```bash
ping fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com
```

If ICMP is unavailable, that does not necessarily mean EFS is unreachable.

A more relevant NFS check is:

```bash
nc -zv fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com 2049
```

---

# 28. Common Problems and Solutions

### Problem 1 – Mount command fails

Check:

```bash
df -h
```

Check security group rules.

Required:

```text
TCP 2049 → NFS
```

---

### Problem 2 – EFS DNS cannot be resolved

Check DNS configuration and VPC DNS settings.

Test:

```bash
nslookup fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com
```

or:

```bash
getent hosts fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com
```

---

### Problem 3 – Permission denied

Check:

```bash
ls -ld /Test1_EFS
```

If needed, review the EFS access point/file permissions and the Linux user permissions.

---

### Problem 4 – Files are not visible from another instance

First verify that both instances are actually mounted to EFS:

```bash
df -Th /Test1_EFS
```

and:

```bash
df -Th /Test2_EFS
```

Also verify that both mount commands point to:

```text
fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com
```

---

# 29. Optional – Persistent EFS Mount

The current mount command creates a mount that may not survive an EC2 reboot.

For persistent mounting, `/etc/fstab` can be configured.

Example:

```bash
sudo vi /etc/fstab
```

Add:

```text
fs-00908b3ec43df8b56.efs.us-east-2.amazonaws.com:/ /Test1_EFS nfs4 nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport,_netdev 0 0
```

Then test:

```bash
sudo mount -a
```

For the other instances, use their respective mount directories:

```text
Test1-2b → /Test2_EFS
Test1-2c → /Test3_EFS
```

---

# 30. Lab Validation Checklist

* [x] Created EC2 instance `Test1-2a`
* [x] Created EC2 instance `Test1-2b`
* [x] Created EC2 instance `Test1-2c`
* [x] Placed instances in `us-east-2a`, `us-east-2b`, and `us-east-2c`
* [x] Created EFS `Test_EFS`
* [x] EFS ID: `fs-00908b3ec43df8b56`
* [x] Configured EFS mount targets
* [x] Configured custom security group
* [x] Allowed NFS TCP `2049`
* [x] Installed NFS client
* [x] Created `/Test1_EFS`
* [x] Created `/Test2_EFS`
* [x] Created `/Test3_EFS`
* [x] Mounted EFS on Test1-2a
* [x] Mounted EFS on Test1-2b
* [x] Mounted EFS on Test1-2c
* [x] Created `RohitApps.txt`
* [x] Created `RohitTools.txt`
* [x] Created `RohitDocs.conf`
* [x] Created `RohitPowerbi.conf`
* [x] Created `RohitTech.txt`
* [x] Verified shared files across instances
* [x] Verified cross-AZ access

---

# 31. Final Result

The completed environment demonstrates an **AWS EFS shared storage architecture across three EC2 instances in three different Availability Zones**.

```text
                  Amazon EFS
                  Test_EFS
                     |
                     |
        fs-00908b3ec43df8b56
                     |
      +--------------+--------------+
      |              |              |
      ↓              ↓              ↓
  us-east-2a     us-east-2b     us-east-2c
      |              |              |
  Test1-2a        Test1-2b       Test1-2c
      |              |              |
      ↓              ↓              ↓
 /Test1_EFS      /Test2_EFS      /Test3_EFS
      |              |              |
      +--------------+--------------+
                     |
                     ↓
              Shared Files
                     |
        +------------+------------+
        |            |            |
   .txt files    .conf files   shared data
```

## Key Learning Outcomes

This lab demonstrates practical knowledge of:

* Amazon EFS
* NFS
* EC2
* Availability Zones
* EFS Mount Targets
* Security Groups
* TCP port 2049
* Linux filesystem mounting
* Shared network storage
* Multi-AZ architecture
* Cross-instance file sharing
* Read/write validation
* EFS troubleshooting
* Persistent filesystem mounting
* Basic AWS infrastructure operations

## Interview Explanation

> "I created an Amazon EFS filesystem in us-east-2 and mounted the same filesystem to three EC2 instances located in us-east-2a, us-east-2b, and us-east-2c. I configured NFS access through a security group on TCP port 2049, installed the NFS client on each instance, created separate local mount points, and mounted the EFS filesystem using NFSv4.1. I then created files from different instances and verified that those files were immediately accessible from the other EC2 instances, demonstrating shared storage across Availability Zones."

This is the key architecture and troubleshooting story to explain in an AWS/Cloud/DevOps interview.
