# AWS ParallelCluster

## Overview
**AWS ParallelCluster** is an open-source cluster management tool used to deploy and manage **High Performance Computing (HPC) clusters** on AWS.

It is a **customer-managed solution** optimized for tightly coupled workloads that require low-latency networking and shared file systems.

---

## Architecture
- **Head node** (scheduler + management)
- **Compute nodes** (scale in/out automatically)
- Uses schedulers such as:
  - Slurm (most common)
  - Torque
  - AWS Batch (optional integration)

---

## Key Features
- Designed for **HPC and MPI workloads**
- Supports tightly coupled parallel jobs
- Custom networking and placement groups
- Customer controls:
  - OS
  - Scheduler
  - Instance types
  - Scaling behavior

---

## Storage Integrations
- Amazon FSx for Lustre (high-throughput workloads)
- Amazon EFS
- Amazon S3

---

## Use Cases
- Scientific research
- Genomics
- Computational fluid dynamics
- Weather modeling
- Financial simulations
- Engineering workloads

---

## Operational Model
- Customer is responsible for:
  - Cluster configuration
  - Scheduler management
  - OS-level access
- More operational overhead than fully managed services

---

## Exam Tip
> Use **AWS ParallelCluster** when the question mentions **HPC, MPI, schedulers (Slurm), tightly coupled workloads, or FSx for Lustre**.
