---
layout: page
title: AI-Based Golf Swing Analysis for Training
description: Keypoint estimation, swing event detection, and multi-view 3D pose estimation from golf swing videos (industry–academia collaboration).
importance: 2
category: work
---

## Summary
This project develops an AI-based golf swing analysis pipeline for training applications. The system estimates pose/keypoints from swing videos, detects major swing events by predicting the frame index of each phase, and reconstructs 3D pose from synchronized multi-view footage (front/side) using camera geometry and multi-view learning. The outcome is a deployable analysis stack designed for scalable coaching and content understanding.

## Motivation
Golf training platforms require consistent, frame-accurate analysis of swing mechanics. Manual labeling of swing phases and posture trajectories is expensive and difficult to scale across players, environments, and camera setups. This work targets reliable automation to support downstream feedback such as posture assessment, timing diagnostics, and event-based coaching.

## Objectives
- **Pose / keypoint estimation** from swing videos for stable per-frame motion understanding.
- **Swing event (sequence) frame estimation** for the eight key phases:
  Address, Takeaway, Backswing, Top, Downswing, Impact, Follow-through, Finish.
- **Multi-view 3D pose estimation** from synchronized front/side videos using camera geometry and multi-view learning.
- **Dataset construction and annotation workflow** to support training and evaluation.

## Method

### 1) 2D Pose / Keypoint Estimation
We build a high-resolution pose estimation pipeline suitable for golf swing footage where motion blur and fast limb/club motion are common.

- Start from a high-resolution, heatmap-based pose formulation.
- Add refinement to reduce pixel quantization and improve temporal stability (less jitter across frames).
- Apply golf-specific robustness strategies (e.g., blur-aware training and thin-structure handling where applicable).

### 2) Swing Event (Sequence) Frame Estimation
Swing event detection is formulated as a temporal modeling problem: estimate per-event probability per frame and select the peak frame for each event.

- Use sequential modeling to capture swing dynamics over time (frame-to-frame dependencies).
- Incorporate pose-derived cues to improve event discrimination (pose-guided temporal features).
- Output a consistent event timeline aligned with the eight swing phases.

### 3) Multi-View 3D Pose Estimation (Front/Side)
We extend analysis beyond 2D by reconstructing 3D pose from synchronized multi-view videos.

- **Camera geometry**: leverage calibrated or estimated camera parameters to enforce geometric consistency across views.
- **Multi-view learning**: learn a representation that fuses front/side observations while maintaining cross-view agreement.
- Produce 3D joint trajectories suitable for downstream coaching signals (e.g., swing plane consistency, joint angle dynamics).

## Data
We built and curated datasets to support training and evaluation across the full pipeline:

- **2D pose/keypoint supervision (frame-level)** for learning stable joint trajectories in swing videos.
- **Swing event labels (video-level)** with frame indices for the eight swing phases:
  Address, Takeaway, Backswing, Top, Downswing, Impact, Follow-through, Finish.
- **Synchronized multi-view samples (front/side)** to enable multi-view 3D pose reconstruction.

We also supported the end-to-end annotation workflow (data selection, labeling guidelines, QA, and iteration with stakeholders) to ensure consistent labeling quality at scale.


## Evaluation (Confidential)
Detailed quantitative results and internal benchmarks are not publicly shareable due to confidentiality constraints.  
Results can be shared upon request under an NDA.

## Deliverables
- Deployable modules for:
  - 2D pose / keypoint estimation
  - Swing event frame estimation
  - Multi-view 3D pose estimation (front/side)
- An annotated dataset and labeling guideline/workflow supporting the above tasks.

## My Role
- Designed the end-to-end pipeline and integration strategy for golf swing video analysis.
- Developed the 2D pose/keypoint estimation component and improved temporal stability for video inputs.
- Implemented multi-view 3D pose estimation from synchronized front/side videos using camera geometry and multi-view learning.
- Led and supported dataset construction and labeling for:
  - **2D pose/keypoint supervision (frame-level)**
  - **Swing event labels (video-level frame indices for the eight phases)**
  - **Synchronized multi-view samples (front/side) for 3D reconstruction**
- Worked closely with stakeholders to define data requirements, labeling guidelines, and quality-control processes.


## Tech Stack
- Heatmap-based 2D pose estimation + refinement
- Temporal sequence modeling for event detection
- Multi-view 3D pose reconstruction (geometry + multi-view learning)
- Dataset curation and annotation workflow
- Deployment-oriented implementation (software deliverables)

---

