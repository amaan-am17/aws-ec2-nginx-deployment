
# EBS Persistence Experiment

## Objective
Verify whether a file stored on an EC2 instance's EBS-backed root filesystem survives a normal stop/start cycle.

## Environment
- Compute: Amazon EC2
- Operating system: Ubuntu Server 24.04 LTS
- Storage: 8 GiB EBS-backed root volume
- Web server: Nginx

## Procedure

### 1. Inspect storage

```bash
lsblk
lsblk -f
df -hT
```

These commands display block devices, filesystem types, mount points, and disk usage.

### 2. Create a test file

```bash
echo "Day 29 - EBS persistence test" > ~/day29-persistence.txt
cat ~/day29-persistence.txt
```

The file was created in the Ubuntu user's home directory on the root filesystem.

### 3. Stop and restart the instance

The EC2 instance was stopped and then started again through the AWS Console. After the instance became available, I reconnected to it.

### 4. Verify persistence

```bash
cat ~/day29-persistence.txt
```

**Observed result:** The file and its contents were still present after the stop/start cycle.

### 5. Verify Nginx

```bash
sudo systemctl is-active nginx
curl -I http://localhost
sudo ss -lntp | grep ':80'
```

**Observed result:** Nginx was active, the local HTTP request returned `200 OK`, and Nginx was listening on port 80.

## Conclusion

The experiment demonstrated that data on the EBS-backed root filesystem persisted through a normal EC2 stop/start cycle.

This does not prove that the data is protected against every failure or accidental deletion. EBS snapshots and other backups are important for recovery, and the root volume's deletion settings matter when an instance is terminated.

## Key Learning

**Persistence is not the same as backup.** EBS provides persistent block storage, while snapshots provide recovery points that can help restore data after certain failures or mistakes.
