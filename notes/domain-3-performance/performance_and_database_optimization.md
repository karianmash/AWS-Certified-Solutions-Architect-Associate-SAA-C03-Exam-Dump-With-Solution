# High-Performance & Database Optimization Notes

## Storage Performance (IOPS)
When a database is struggling with **slow inserts/writes** (high latency), the bottleneck is usually disk I/O.

### General Purpose SSD (gp2/gp3)
- Performance is tied to the size of the volume (for gp2) or has a baseline (for gp3).
- Good for most workloads but can suffer from "IOPS exhaustion" during heavy spikes.

### Provisioned IOPS SSD (io1/io2)
- You pay for a **guaranteed** amount of performance (IOPS).
- **Correct Answer (Option A)**: This is the only way to "brute force" a fix for storage latency when instance scaling (CPU/RAM) isn't the problem.

---

## What about the other options?
- **Read Replicas (Option B)**: These **only** scale *Reads*. They actually add a tiny bit of overhead to *Writes* because data must be replicated.
- **Multi-AZ (Option C)**: This is for **Resilience/High Availability**, not performance. In fact, Multi-AZ can slightly *increase* write latency because it uses synchronous replication.
- **Instance Scaling (Option D)**: If the storage is the bottleneck, adding more CPU or RAM won't help the disks spin faster!

> [!IMPORTANT]
> **Exam Tip**: 
> - Slow **Reads**? -> Use **Read Replicas** or **ElastiCache**.
> - Slow **Writes** (Disk)? -> Use **Provisioned IOPS**.
