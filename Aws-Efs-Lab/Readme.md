# ☁️ Amazon EFS Lab

### Mount one shared file system on two EC2 instances

**☁️ AWS EFS | 🖥️ EC2 | 🐧 Amazon Linux 2023 / 2 | 🟢 Beginner**

*Think of EFS as a shared network folder for your EC2 instances.*

---

## 📑 Table of Contents

- [What is EFS?](#-what-is-efs)
- [EFS vs EBS vs S3](#-efs-vs-ebs-vs-s3)
- [Key Terms](#-key-terms)
- [Architecture](#-architecture)
- [Lab Goal](#-lab-goal)
- [Step-by-Step Lab](#-step-by-step-lab)
- [Troubleshooting](#-troubleshooting)
- [Cleanup](#-cleanup)
- [References](#-references)

---

## 📦 What is EFS?

**Amazon Elastic File System (EFS)** is a managed, shared file system for **Linux** servers in AWS. Multiple EC2 instances can mount the same EFS file system at the same time and work with the same files.

> 💡 If Server 1 saves a file to EFS, Server 2 can read that file through its own mount.

EFS **grows automatically** as you store more data, so you don't choose a fixed disk size.

---

## ⚖️ EFS vs EBS vs S3

| Storage | What it is | Typical use |
|---------|-----------|-------------|
| **EBS** | A disk volume generally attached to one EC2 instance | OS, application, or database disk |
| **EFS** | A shared file system multiple Linux EC2 instances can mount | Shared uploads, documents, application files |
| **S3** | Object storage accessed via APIs or web requests | Backups, images, archives, static files |

---

## 📚 Key Terms

| Term | Meaning |
|------|---------|
| **File system** | The shared EFS storage itself |
| **Mount target** | A network endpoint in your VPC that EC2 instances use to reach EFS (created per subnet / Availability Zone) |
| **Mount** | Connecting EFS to a Linux directory, such as `/mnt/efs` |
| **NFS** | The network file-sharing protocol EFS uses, over **TCP port 2049** |
| **Security group** | A virtual firewall. The EC2 group allows SSH; the mount target's group allows NFS |

---

## 🏗️ Architecture

```
                     ┌──────────────────────────┐
                     │         AWS VPC          │
                     │                          │
   ┌───────────────┐ │   ┌──────────────────┐   │ ┌───────────────┐
   │ EFS-Server-1  │─┼──▶│                  │◀──┼─│ EFS-Server-2  │
   │  /mnt/efs     │ │   │  Mount Target(s) │   │ │  /mnt/efs     │
   └───────────────┘ │   │  (NFS · 2049)    │   │ └───────────────┘
      EFS-EC2-SG     │   └────────┬─────────┘   │      EFS-EC2-SG
                     │            │             │
                     │     ┌──────▼───────┐     │
                     │     │  EFS File    │     │
                     │     │  System      │     │
                     │     │ (EFS-Mount-SG)│    │
                     │     └──────────────┘     │
                     └──────────────────────────┘
```

---

## 🎯 Lab Goal

Using two EC2 instances — **EFS-Server-1** and **EFS-Server-2** — you will:

1. Create one EFS file system
2. Mount it on both instances
3. Confirm a file written on one is visible on the other

> **Assumes:** both instances run Amazon Linux 2023 or Amazon Linux 2 and are in the same VPC as EFS.

---

## 🧪 Step-by-Step Lab

### ✅ Step 1: Check your EC2 instances

In the EC2 console, confirm:

- [ ] Both instances are **running**
- [ ] Both are in the **same VPC**
- [ ] You can **SSH** into each
- [ ] Both are **Linux** (EFS does not mount on Windows)

> ℹ️ Your `EFS-EC2-SG` SSH rule (port 22 from *My IP*) is for logging in only. It does **not** allow EFS traffic.

### 🗂️ Step 2: Create the EFS file system

1. Open **Amazon EFS** in the AWS console
2. Choose **Create file system**
3. Select the **same VPC** as your EC2 instances
4. Use default settings for this practice lab and create it
5. Wait until the file system and mount targets are **available**
6. Copy the **file system ID** (e.g. `fs-0123456789abcdef0`)

### 🔐 Step 3: Allow NFS traffic to EFS

1. Go to **EC2 → Security Groups** and create `EFS-Mount-SG` in the same VPC
2. Add this inbound rule:

   | Type | Port | Source |
   |------|------|--------|
   | NFS | 2049 | `EFS-EC2-SG` |

3. In **EFS**, edit the mount targets' security groups and select `EFS-Mount-SG`

> 🔒 Using the EC2 security group as the source avoids opening NFS to every IP address.
> If you used the VPC default security group instead, edit that group's inbound rule, and make sure it is the one attached to the mount targets.

### 💻 Step 4: Install the EFS client and mount on Server 1

SSH into **EFS-Server-1** and run:

```bash
sudo dnf install -y amazon-efs-utils || sudo yum install -y amazon-efs-utils
sudo mkdir -p /mnt/efs
sudo mount -t efs -o tls fs-REPLACE_WITH_YOUR_ID:/ /mnt/efs
```

Example:

```bash
sudo mount -t efs -o tls fs-0123456789abcdef0:/ /mnt/efs
```

> 🛡️ `-o tls` encrypts data in transit between the instance and EFS.

### ✍️ Step 5: Write a test file from Server 1

```bash
echo "Hello from EFS-Server-1" | sudo tee /mnt/efs/lab.txt
ls -l /mnt/efs
```

### 🔁 Step 6: Mount EFS on Server 2

SSH into **EFS-Server-2** and run the same commands with the **same file system ID**:

```bash
sudo dnf install -y amazon-efs-utils || sudo yum install -y amazon-efs-utils
sudo mkdir -p /mnt/efs
sudo mount -t efs -o tls fs-REPLACE_WITH_YOUR_ID:/ /mnt/efs
```

### 🎉 Step 7: Confirm the file is shared

On **EFS-Server-2**:

```bash
cat /mnt/efs/lab.txt
```

Expected output:

```
Hello from EFS-Server-1
```

✅ Both instances are using the same EFS file system.

---

## 🛠️ Troubleshooting

| Problem | Likely cause / fix |
|---------|--------------------|
| Mount hangs or times out | Check mount target status, VPC, and security groups. `EFS-Mount-SG` must allow inbound **TCP 2049** from the EC2 security group |
| `No such file or directory` | Make sure `/mnt/efs` exists and the file system ID is correct |
| `unknown filesystem type 'efs'` | `amazon-efs-utils` is not installed. Re-run the install command |
| SSH works but EFS doesn't | SSH uses port **22**, EFS uses **2049**. Allowing one does not allow the other |
| Different Linux distro | Install commands vary. These are for Amazon Linux 2023 / 2 |

---

## 🧹 Cleanup

> ⚠️ EFS storage and mount targets may incur charges while they exist.

1. Unmount on **both** instances:
   ```bash
   sudo umount /mnt/efs
   ```
2. In the EFS console, **delete the file system** (mount targets may need to be removed as part of deletion)
3. In the EC2 console, **terminate** the lab instances
4. **Delete** the lab security groups only after they are no longer attached to an instance or mount target

---

## 🔗 References

- [AWS: Create an EFS file system](https://docs.aws.amazon.com/efs/latest/ug/creating-using-create-fs.html)
- [AWS: EFS security group rules](https://docs.aws.amazon.com/efs/latest/ug/network-access.html)
- [AWS: Install the EFS client](https://docs.aws.amazon.com/efs/latest/ug/installing-amazon-efs-utils.html)
- [AWS: Mount EFS on Linux](https://docs.aws.amazon.com/efs/latest/ug/mounting-fs.html)

---

⭐ Happy learning, and don't forget the cleanup! ☁️
