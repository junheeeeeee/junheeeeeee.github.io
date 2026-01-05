---
layout: page
title: Vision AI for Industrial Safety
description: Real-time 3D human pose estimation and open-vocabulary object detection using vision–language learning (R&D project).
importance: 4
category: work
---

## Summary
This project develops two core vision AI capabilities for industrial environments:

1) **Real-time 3D Human Pose Estimation (3D HPE)** from video to monitor worker posture and support safety-oriented alerts and explanations. :contentReference[oaicite:2]{index=2}  
2) **Open-Vocabulary / Open-Set Object Detection (OVOD)** leveraging cross-modal vision–language learning to detect novel objects by adjusting text prompts rather than retraining the detector. :contentReference[oaicite:3]{index=3}

The goal is to build adaptable, deployment-ready models that generalize across diverse sites, tasks, and changing object requirements.

## Motivation
Industrial sites are highly dynamic: worker posture risks vary by task, and the set of objects to detect changes frequently across environments. Traditional pipelines require costly data collection and retraining whenever conditions shift. This project focuses on (a) robust posture understanding in real time and (b) language-driven adaptability for object detection.

## Objectives
### 1) 3D Human Pose Estimation (Video → 3D Joints)
- Predict 3D joint coordinates from real-time video streams to support posture monitoring and safety guidance. :contentReference[oaicite:4]{index=4}  
- Improve accuracy and robustness to be applicable across diverse industrial scenarios. :contentReference[oaicite:5]{index=5}  

### 2) Open-Vocabulary / Open-Set Object Detection (Vision + Language)
- Extend closed-set object detection to open-set settings by integrating **vision–language cross-modal information**. :contentReference[oaicite:6]{index=6}  
- Enable rapid adaptation to new environments/objects by **editing language inputs** instead of replacing or retraining the base detector. :contentReference[oaicite:7]{index=7}  

## Method

### Workstream A: Real-Time 3D Human Pose Estimation
- **Input/Output**: video frames → 3D joint coordinates (per frame / temporal sequence).
- **Modeling strategy**
  - Evaluate end-to-end 3D estimation and/or two-stage pipelines (2D keypoints → 3D lifting), selecting the most deployable approach for real-time constraints.
  - Add temporal stabilization and filtering strategies to reduce jitter and improve consistency in streaming settings.
- **System integration**
  - Provide posture signals that can be used for downstream safety logic (e.g., risky bending, hazardous reach, unsafe handling posture), enabling alerts and explanatory feedback.

### Workstream B: Open-Vocabulary / Open-Set Object Detection via Vision–Language Learning
- **Core idea**
  - Fuse visual features with language embeddings to detect objects beyond a fixed set of trained categories. :contentReference[oaicite:8]{index=8}  
- **Adaptation without retraining**
  - When the target set changes (new site / new objects), update detection behavior through **text prompts or language inputs** rather than retraining the detector. :contentReference[oaicite:9]{index=9}  
- **Deployment focus**
  - Maintain a strong closed-set baseline while enabling open-set expansion through language conditioning.

## Data & Annotation (High-Level)
- **3D HPE**
  - Video data annotated or prepared to support 3D joint supervision and evaluation for posture-centric tasks. :contentReference[oaicite:10]{index=10}  
- **OVOD**
  - Detection datasets supporting both closed-set performance and open-set evaluation, with text descriptions/class names used as language supervision. :contentReference[oaicite:11]{index=11}  

(Details such as data sources, labeling policies, and internal evaluation splits are omitted due to confidentiality.)

## Deliverables
- A real-time 3D pose estimation module that outputs 3D joints from video for posture monitoring and safety applications. :contentReference[oaicite:12]{index=12}  
- An open-vocabulary object detection module that integrates vision–language signals and supports language-only adaptation to new objects/environments. :contentReference[oaicite:13]{index=13}  
- Dataset/annotation guidelines and a reproducible training–evaluation recipe for both workstreams (internal use).

## Evaluation (Confidential)
Quantitative results and internal benchmarks are not publicly shareable due to confidentiality constraints.  
Results can be shared upon request under an NDA.

## My Role (edit as needed)
- Contributed to end-to-end project planning and technical design across both workstreams (3D HPE and OVOD). :contentReference[oaicite:14]{index=14} :contentReference[oaicite:15]{index=15}  
- Supported dataset construction and annotation workflows, including labeling requirements and quality checks.
- Collaborated with stakeholders to iterate on requirements and deployability constraints for real-world industrial environments.

## Tech Stack (high-level)
- 3D human pose estimation from video (real-time posture monitoring)
- Vision–language cross-modal learning for open-vocabulary detection
- Deployment-oriented model integration and data/annotation pipelines

---
