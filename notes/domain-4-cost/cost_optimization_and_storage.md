# Cost Optimization & Storage Classes

## S3 Storage Classes Cheat Sheet
Choosing the right storage class is the #1 way to optimize costs in AWS.

### The "Unpredictable" King (Option B)
- **S3 Intelligent-Tiering**: The **correct answer** for unpredictable or changing access patterns. 
- It automatically moves objects between a "Frequent Access" tier and an "Infrequent Access" tier based on usage.
- **Why not A?** S3 Standard is too expensive for rarely accessed data.
- **Why not C?** S3 One Zone-IA fails the requirement to be "resilient to the loss of an Availability Zone."
- **Why not D?** S3 Glacier is for archival. Retrieving data from Glacier is slow (minutes to hours) and can be expensive if done frequently.

## Key Cost Optimization Concepts
- **Spot Instances**: Use for stateless, fault-tolerant workloads (e.g., batch processing).
- **Reserved Instances / Savings Plans**: Use for steady-state workloads (e.g., production DBs).
- **S3 Lifecycle Policies**: Automate the transition of data to cheaper tiers (Standard -> IA -> Glacier) based on age.

> [!TIP]
> **Exam Strategy**: 
> - "Unpredictable pattern"? -> **Intelligent-Tiering**.
> - "Archive/Long-term"? -> **Glacier**.
> - "Non-critical/reproducible data"? -> **One Zone-IA**.
