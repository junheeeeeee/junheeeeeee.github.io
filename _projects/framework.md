---
layout: page
title: 3D Human Pose Estimation on a Proprietary Training Framework
description: Feasibility study and prototype design for implementing modern 3D pose estimation models on an enterprise in-house deep learning framework.
importance: 3
category: work
---

## Summary
This project evaluated the feasibility of implementing modern **3D human pose estimation** algorithms using an **enterprise in-house deep learning framework**. We surveyed representative model architectures and learning paradigms, assessed whether key components (e.g., transformer blocks) can be reproduced in the framework, and identified system-level limitations encountered during practical experimentation. Based on the findings, we proposed actionable framework improvements to better support 3D pose estimation workloads.

## Background & Motivation
3D human pose estimation is a core capability for motion understanding in video analytics, human–computer interaction, and sports/health applications. While PyTorch is commonly used for research prototyping, this project aimed to validate whether an in-house framework can support state-of-the-art 3D pose estimation pipelines in production-oriented environments.

## Objectives
- Summarize major **3D pose estimation methodologies** and representative network designs.
- Review commonly used **datasets and evaluation protocols** for 3D pose estimation.
- Determine feasibility of implementing recent models in the framework and identify blockers.
- Propose **framework-level improvements** (engineering solutions) to close key gaps.

## Method

### 1) Methodology Review: End-to-End vs. Two-Stage
We organized 3D pose estimation methods into two categories:
- **End-to-End**: directly infer 3D pose from RGB images/videos.
- **Two-Stage**: estimate 2D keypoints first, then lift to 3D pose.

### 2) Dataset & Benchmark Landscape
We reviewed widely used benchmarks to understand data requirements and generalization constraints, including:
- Human3.6M
- MPI-INF-3DHP

### 3) Implementation Feasibility on the In-House Framework
We assessed whether the framework can implement key building blocks used in modern 3D pose networks.

- **Transformer-based architectures**
  - Evaluated support for embeddings, attention blocks, and MLP components commonly used in transformer-based 3D pose models.
  - Concluded that transformer-centric 3D pose networks are largely implementable given sufficient operator and tensor support.

- **Models with non-standard train/inference graphs**
  - Some formulations require different computational flows for training vs. inference.
  - Proposed enabling explicit inference-graph specification to support such methods without invasive engine changes.

## Key Findings
- The framework can represent many common model structures, and transformer-based 3D pose models appear feasible.
- However, **tensor-shape manipulation and system-level constraints** can become critical blockers for end-to-end 3D pose workflows.
- Due to environment/build and tensor-handling limitations observed during experimentation, we did not publish direct performance comparisons.

## Recommendations
- Improve robustness and ergonomics for **tensor shape operations** and build stability to support 3D pose pipelines end-to-end.
- Provide official support for **separate inference graphs** when training and inference differ.
- Establish a validated 3D pose **reference recipe** (preprocessing, metrics, reproducible runs) within the framework.

## Deliverables
- A structured survey of 3D pose estimation methodologies, datasets, and representative architectures.
- A feasibility analysis identifying implementable components and framework blockers.
- Engineering proposals for inference-graph handling and system-level improvements.

## My Role
- Researched and summarized state-of-the-art 3D pose estimation methods and benchmark datasets.
- Assessed implementation feasibility of modern architectures (including transformer-based components) within an enterprise in-house framework.
- Identified practical framework constraints and proposed concrete engineering solutions.
- Collaborated with partner engineers and stakeholders through iterative review cycles.

## Tech Stack
- Proprietary in-house deep learning / training framework
- 3D human pose estimation (end-to-end and two-stage paradigms)
- Transformer-based temporal/spatial modeling
- Benchmark analysis (Human3.6M, MPI-INF-3DHP)

---
