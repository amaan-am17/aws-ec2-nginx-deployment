

# AWS EC2 Web Server Deployment and EBS Persistence

## Project Overview
Hands-on AWS project covering EC2 deployment, Nginx configuration, networking, security groups, Linux troubleshooting, and EBS persistence.

## Technologies Used
- Amazon EC2
- Ubuntu Server 24.04 LTS
- Nginx
- Amazon EBS
- Amazon VPC and security groups

## Work Completed

### EC2 Deployment
- Launched an Ubuntu EC2 instance using the t2.micro instance type.
- Connected using EC2 Instance Connect.
- Reviewed instance networking and storage.

### Nginx Deployment
- Installed and started Nginx.
- Created a custom web page.
- Verified the service was active and enabled.
- Confirmed an HTTP 200 OK response using curl.
- Verified Nginx was listening on port 80.

### Networking and Security
- Configured inbound HTTP access on TCP port 80.
- Reviewed SSH access restrictions.
- Examined the VPC CIDR, route table, internet gateway, and network ACL.
- Learned the differences between security groups and network ACLs.

### EBS Persistence Experiment
- Inspected disks and filesystems using lsblk and df -hT.
- Created a test file in the Ubuntu user's home directory.
- Stopped and restarted the EC2 instance.
- Reconnected and confirmed the test file persisted.
- Verified that Nginx remained operational.

## Useful Linux Commands

```bash
lsblk
lsblk -f
df -hT
systemctl is-active nginx
systemctl is-enabled nginx
curl -I http://localhost
sudo ss -lntp
```

## Key Learnings
- EC2 deployment and Linux web-server administration.
- HTTP connectivity and security group configuration.
- Public versus private IPv4 addresses.
- Route tables, internet gateways, and network ACLs.
- EBS persistence versus snapshots and backups.
- Service, network, and storage troubleshooting.

## Security
Never commit AWS credentials, access keys, private keys, passwords, or other secrets. Review screenshots before publishing them.

## Project Status
Initial EC2 deployment, Nginx validation, networking review, and EBS stop/start persistence experiment completed.

# aws-ec2-nginx-deployment
Hands-on AWS project covering EC2, Nginx deployment, networking, EBS persistence, and troubleshooting.

