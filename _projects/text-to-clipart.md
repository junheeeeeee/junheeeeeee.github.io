---
layout: page
title: Text-to-ClipArt Video Generation System
description: From Korean educational text to ClipArt-style images and character animations (industry–academia collaboration).
importance: 1
category: work
---

## Summary
We built an end-to-end system that turns **Korean educational sentences** into **ClipArt-style visual content**, and further converts generated characters into **animated videos** via pose estimation and animation transfer. The project targets scalable content creation for digital learning materials.

## Problem
Educational platforms often require a large volume of **pedagogical illustrations** and **lightweight animations** aligned with text-based curricula. Manual asset creation is expensive and does not scale well across topics, grades, and cultural contexts.

## Approach
The system is composed of three stages:

1. **Prompt Transformation**
   - Translate Korean inputs into English.
   - Normalize into a prompt format better suited for ClipArt-style generation (e.g., style tokens, constraints, and object-centric phrasing).

2. **Text-to-ClipArt Image Generation**
   - Use a diffusion-based text-to-image model adapted for ClipArt-like outputs.
   - Focus on clean silhouettes, minimal texture, and classroom-friendly composition.

3. **Pose Estimation & Animation Generation**
   - Estimate character pose (single image or sequences, depending on the scenario).
   - Convert pose signals into animation by applying a motion/pose-driven transformation pipeline.

## Data
We constructed datasets for both image generation and animation:

- **Caption dataset**
  - Designed prompts/captions for educational semantics and ClipArt style consistency.
  - Included domain-specific categories commonly appearing in classroom materials.

- **Image dataset**
  - Curated and categorized images to support ClipArt appearance and robust filtering (e.g., usable vs. unusable).
  - Emphasized clean backgrounds and consistent character depiction.

- **Pose dataset**
  - Aggregated pose supervision from public pose datasets and synthetically generated pose samples.
  - Extended coverage to diverse occupations/actions frequently used in educational settings.

## Key Challenges
- **Safety filtering artifacts**
  - Automated safety checkers can occasionally produce degenerate outputs (e.g., black images), requiring mitigation strategies.

- **Out-of-distribution prompts**
  - Rare, culturally specific, or highly compositional Korean inputs sometimes fall outside training distribution, leading to unrealistic or degraded results.

- **Translation fidelity**
  - Certain Korean educational/cultural terms do not map cleanly into English prompts, motivating domain-adapted translation or bilingual prompt engineering.

- **Prompt sensitivity**
  - Small prompt edits can cause large visual changes, demanding careful prompt normalization and template design.

## Results (Qualitative)
The system produces:
- ClipArt-style images aligned with Korean textual descriptions.
- Pose-driven character animations suitable for short educational clips.

(You can add quantitative metrics here if you have evaluation results: preference rate, CLIP score trends, human rating, success rate by category, etc.)

## Demo
- **Live demo / internal demo link:** (add your URL)
- **Example gallery:** (you will insert images/videos here)

## My Role
- Designed the overall pipeline and system integration strategy.
- Developed prompt transformation and dataset construction protocol.
- Built training/evaluation loop and performed error analysis on failure modes (filtering, translation, OOD prompts).
- Coordinated iteration cycles with stakeholders for educational usability.

## Tech Stack
- Diffusion-based text-to-image generation
- Neural machine translation for Korean→English
- Human pose estimation
- Animation/motion transfer pipeline
- Deployment: (Gradio / web demo / internal serving)

## Future Work
- Domain-adapted bilingual prompting (Korean-aware prompt templates)
- Expanded training distribution for classroom-specific concepts and compositions
- Robust safety-filter mitigation and fallback generation strategies
- Quantitative evaluation protocol tailored to educational illustration quality

---
