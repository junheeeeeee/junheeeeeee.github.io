---
layout: page
title: Vision AI for Industrial Safety
description: Real-time 3D human pose estimation and open-vocabulary object detection using vision–language learning (R&D project).
importance: 2
category: work
---

## Summary
This project develops two core vision AI capabilities for industrial environments:
1) **Real-time 3D Human Pose Estimation (3D HPE)** from video to monitor worker posture and support safety-oriented reasoning.
2) **Open-Vocabulary Object Detection (OVOD)** using vision–language learning to detect novel objects through text prompts rather than retraining.

## Motivation
Industrial sites are highly dynamic: worker posture risks vary by task, and the set of objects to detect changes frequently across environments. Traditional pipelines often require costly data collection and retraining whenever conditions shift. This project focuses on robust posture understanding in real time and language-driven adaptability for object detection.

## Objectives
### 1) 3D Human Pose Estimation (Video → 3D Joints)
- Predict 3D joint coordinates from real-time video streams to support posture monitoring.
- Improve robustness to varied viewpoints, motion blur, occlusions, and diverse workwear/lighting conditions.

### 2) Open-Vocabulary Object Detection (Vision + Language)
- Extend closed-set object detection to open-vocabulary settings by integrating vision–language representations.
- Enable rapid adaptation to new objects/environments by editing language inputs (text prompts) instead of retraining the detector.

## Method

### Workstream A: Real-Time 3D Human Pose Estimation
- **Input/Output**: video frames → 3D joint coordinates (per frame / temporal sequence).
- **Modeling strategy**
  - Evaluate end-to-end 3D estimation and two-stage pipelines (2D keypoints → 3D lifting) and select an approach suitable for real-time constraints.
  - Add temporal stabilization to reduce jitter and improve consistency in streaming conditions.
- **Integration**
  - Provide posture signals that can be used by downstream safety logic (e.g., risky bending, hazardous reach, unsafe lifting posture), enabling alerts and explanatory feedback.

### Workstream B: Open-Vocabulary Object Detection via Vision–Language Learning
- **Core idea**
  - Combine visual features with language embeddings to detect objects beyond a fixed set of trained categories.
- **Adaptation without retraining**
  - When target objects change, update detection behavior through prompt engineering (text descriptions/class names) instead of retraining the model.
- **Deployment focus**
  - Maintain strong closed-set performance while enabling open-vocabulary expansion through language conditioning.

## Data & Annotation (High-Level)
- **3D HPE**
  - Video data prepared to support 3D joint supervision and posture-centric evaluation.
- **OVOD**
  - Detection data supporting both closed-set performance and open-vocabulary evaluation, with text descriptions used as language supervision.

(Details such as data sources, labeling policies, and internal evaluation splits are omitted due to confidentiality.)

## Deliverables
- A real-time 3D pose estimation module that outputs 3D joints from video for posture monitoring applications.
- An open-vocabulary object detection module that supports language-only adaptation to new objects/environments.
- Dataset/annotation guidelines and a reproducible training/evaluation recipe for internal use.

## Evaluation (Confidential)
Quantitative results and internal benchmarks are not publicly shareable.
Results can be shared upon request under an NDA.

## My Role
- Contributed to technical design across both workstreams (3D HPE and OVOD).
- Supported dataset construction and annotation workflows, including labeling requirements and quality checks.
- Collaborated with stakeholders to iterate on requirements and deployment constraints for industrial environments.

## Tech Stack (high-level)
- Real-time 3D human pose estimation from video
- Vision–language cross-modal learning for open-vocabulary detection
- Deployment-oriented model integration and data/annotation pipelines

---

