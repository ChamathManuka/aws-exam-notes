# AWS Step Functions

## Overview
**AWS Step Functions** is a serverless orchestration service used to build **multi-step workflows** that coordinate AWS services.

It is designed for **process orchestration**, not for single recurring or cron-style jobs.

---

## Core Capabilities
- Step-by-step execution
- Maintains workflow **state**
- Built-in:
  - Retries
  - Timeouts
  - Error handling
  - Catch / Finally logic
- Visual workflow definition using **Amazon States Language (ASL / JSON)**

---

## Workflow Types
- **Standard Workflows**
  - Long-running
  - Exactly-once execution
- **Express Workflows**
  - High-throughput
  - Short-lived
  - At-least-once execution

---

## Scheduling
- Can schedule tasks using:
  - `Wait` states
  - EventBridge Scheduler (recommended)
- Not designed for simple cron jobs

---

## Integrations
- AWS Lambda
- Amazon ECS / EKS
- AWS Batch
- Amazon DynamoDB
- Amazon S3
- Amazon SageMaker

---

## Relationship with EventBridge
- **Step Functions and EventBridge complement each other**
- EventBridge:
  - Triggers workflows
- Step Functions:
  - Orchestrates multi-step logic

They are **used together, not as replacements**.

---

## Use Cases
- Order processing
- Microservice orchestration
- Data pipelines
- ML workflows
- Approval workflows
- Long-running business processes

---

## When NOT to Use Step Functions
- Single-step tasks
- Simple cron scheduling
- Ultra-low latency workloads

---

## Exam Tip
> Choose **AWS Step Functions** when the question mentions **workflow orchestration, retries, state management, or multi-step processes**.
