---
layout: page
title: AI-Based Golf Swing Analysis for Training
description: Keypoint estimation and swing event detection from golf swing videos (industry–academia collaboration).
importance: 1
category: work
---

## Summary
This project developed an AI-based golf swing analysis pipeline for training applications. The system estimates **2D human keypoints (and clubhead-related cues)** from swing videos and detects **major swing events** by predicting the frame index of each phase in a swing sequence. The deliverables were implemented as deployable software components and accompanied by an annotated dataset. :contentReference[oaicite:1]{index=1}

<!-- TODO: Insert an overview figure of the pipeline -->

## Motivation
Golf training platforms rely on consistent, frame-accurate analysis of swing mechanics. Manual annotation of swing phases and joint trajectories is time-consuming and difficult to scale. This work aimed to provide a robust, automatic pipeline that supports downstream feedback such as posture assessment, timing diagnostics, and event-based coaching.

## Objectives
1. **Pose / keypoint estimation from swing videos**
   - Estimate 2D joint keypoints across frames and return coordinate metadata per frame.
   - Extend standard pose estimation to better handle golf-specific factors (e.g., club motion, blur, and small fast-moving parts). :contentReference[oaicite:2]{index=2}

2. **Swing event (sequence) frame estimation**
   - Detect the frame index of eight key swing events:
     **Address, Takeaway, Backswing, Top, Downswing, Impact, Follow-through, Finish**. :contentReference[oaicite:3]{index=3}

3. **Dataset construction and annotation**
   - Build an annotation workflow and produce labeled data supporting pose estimation and swing event modeling. :contentReference[oaicite:4]{index=4}

## Method

### 1) Pose / Keypoint Estimation
We started from a high-resolution pose estimation baseline and introduced adaptations to improve stability and precision in golf swing footage.

- **Baseline**
  - A high-resolution representation approach (HRNet-style) that preserves fine spatial detail.
  - Limitation: standard person-centric pipelines may not directly model golf-specific cues such as the clubhead.

- **Proposed pose network**
  - A scalable feature-aggregation architecture designed to reduce quantization errors and enable flexible model scaling.
  - Multi-stage supervision using intermediate heatmap predictions (weighted training across blocks) for stable convergence.

- **Refinement for keypoint precision**
  - An additional refinement module predicts a 2D offset vector to correct pixel-level errors from heatmap argmax selection.
  - This helps reduce visible jitter and discretization artifacts in video outputs. :contentReference[oaicite:5]{index=5}

- **Training augmentations (golf-specific)**
  - Heatmap augmentation along the club region to guide learning under blur and thin-structure conditions.
  - Blur augmentation applied to the club region to improve robustness to motion blur. :contentReference[oaicite:6]{index=6}

<!-- TODO: Insert a figure comparing baseline vs. refined pose outputs -->

### 2) Swing Event (Sequence) Frame Estimation
Swing event detection was formulated as a temporal modeling problem: estimate the probability of each event per frame and select the highest-confidence frame for each event.

- **Baseline**
  - A SwingNet-style model (LSTM-based) using frame-level visual features.
  - Limitation: relying on global image features can be sensitive to background and may provide weak evidence for specific swing events.

- **Pose-guided event detection (proposed)**
  - Inject pose guidance by concatenating **pose heatmaps** with frame-level image features.
  - Use a residual approach to retain useful frame information while integrating pose cues.
  - Feed the fused representation into an LSTM to learn temporal dynamics and produce per-event probabilities per frame. :contentReference[oaicite:7]{index=7}

<!-- TODO: Insert a figure illustrating event timeline and predicted event frames -->

### 3) Dataset & Annotation Pipeline
A dedicated annotation workflow was designed to support both pose estimation and swing event modeling at scale.

- Video selection and preprocessing (front/side views), frame extraction, and rotation normalization for labeling efficiency.
- Swing event frame selection: scan long sequences to identify the eight events across videos.
- Dense annotations on selected frames, including **bounding boxes, segmentation, and pose keypoints**, coordinated by a team-based process. :contentReference[oaicite:8]{index=8}

## Data
The project used a proprietary/partner dataset containing both **frame-level pose supervision** and **video-level swing sequences** (front and side views). The dataset was split into training/testing sets for both pose estimation and event detection tasks, and it was expanded through annotation and curation workflows described above. :contentReference[oaicite:9]{index=9}

## Results
We evaluated two core capabilities:

1. **Pose estimation quality**
   - Metric: **PCKh@0.5** (Percentage of Correct Keypoints, head-normalized).
   - The final models achieved performance above the target threshold, and refinement improved stability/accuracy. :contentReference[oaicite:10]{index=10}

2. **Swing event frame detection**
   - Metric: **PCE** (Percentage of Correct Events) over the eight swing events.
   - The pose-guided approach improved event detection compared to the baseline and exceeded the target performance level. :contentReference[oaicite:11]{index=11}

<!-- TODO: Insert your quantitative table/plots (PCKh/PCE) here -->
<!-- TODO: Insert qualitative examples (pose overlays, event timelines) here -->

## Deliverables
- Source code for:
  - Pose / keypoint estimation module (deployable)
  - Swing event frame estimation module (deployable)
- Completed annotated dataset supporting pose, detection, and sequencing tasks. :contentReference[oaicite:12]{index=12}

## My Role (edit as needed)
- Designed and implemented the overall pipeline for swing video analysis.
- Developed and/or trained the pose estimation model and refinement strategy.
- Built the pose-guided swing event detection model and evaluation pipeline.
- Led dataset curation and supported the annotation workflow with stakeholders.

## Tech Stack (high-level)
- Deep learning–based 2D pose estimation (heatmap + refinement)
- Temporal event modeling (pose-guided features + LSTM)
- Dataset curation and large-scale annotation workflow
- Deployment-oriented implementation (software deliverables)

## Future Work
- **3D pose estimation from multi-view (front/side) videos** using camera geometry and multi-view learning.
- **Real-time ball motion analysis** for putting and trajectory-based feedback.
- Robust real-world deployment improvements (latency, stability under motion blur, and domain shift). :contentReference[oaicite:13]{index=13}
