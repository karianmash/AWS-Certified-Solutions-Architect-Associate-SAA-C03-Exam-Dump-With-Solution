# Resilience & Shared Storage Notes

## The Problem: Data Silos (EBS)
In a Multi-AZ architecture, standard **EBS volumes** are locked to a single Availability Zone. 
- If you have Instance A in AZ-1 and Instance B in AZ-2, they cannot share the same EBS volume.
- Users hitting Instance A see different data than those hitting Instance B.

## The "Sticky Sessions" Trap (Option B)
While Sticky Sessions (Session Affinity) on an ALB can make a user "stick" to one instance, it is **NOT** a resilient solution because:
1. **No Failover**: If Instance A fails, the user is sent to Instance B but their files are still stuck on Instance A's EBS volume.
2. **Scalability Issues**: It prevents the Load Balancer from distributing traffic evenly.

## The Solution: Amazon EFS (Option C)
**Amazon EFS (Elastic File System)** is the standard "Architectural" answer for shared storage between EC2 instances because:
- **Shared Access**: Thousands of instances can mount the same EFS volume simultaneously across different AZs.
- **Regional Resilience**: EFS stores data redundantly across multiple AZs by default.
- **Managed Service**: No need to manage replication scripts.

> [!TIP]
> **Exam Strategy**: If a question mentions "shared storage between multiple EC2 instances" or "Multi-AZ consistency," look for **EFS** for Linux or **FSx** for Windows.
