---
layout: page
title: Text-to-ClipArt Video Generation System
description: From Korean educational text to ClipArt-style images and pose-driven character animations (industry–academia collaboration).
img: /assets/img//text-to-clipart/penguin2.gif
importance: 1
category: work
---

## Summary
We developed an end-to-end pipeline that converts **Korean educational sentences** into **ClipArt-style visual content** and further animates characters into short **pose-driven videos**. The goal is to enable scalable asset creation for digital learning materials.

## Motivation
Educational platforms require a large volume of **pedagogical illustrations** and **lightweight animations** aligned with curricula. Manual asset creation is costly and does not scale across topics, grades, or culturally specific content.

## Method
The system consists of three stages:

1. **Prompt Transformation**
   - Translate Korean inputs into English.
   - Normalize the text into a prompt format suitable for ClipArt-style generation (e.g., object-centric phrasing and style constraints).

2. **Text-to-ClipArt Image Generation**
   - Generate ClipArt-style images using a diffusion-based text-to-image model adapted for classroom-friendly outputs.
   - Emphasize clean shapes, minimal texture, and consistent character appearance.

3. **Pose Estimation & Animation**
   - Given either (i) an existing character image or (ii) a generated ClipArt character, estimate character pose.
   - Produce an animated sequence using a pose-driven animation pipeline.

## Data
We constructed datasets for both image generation and animation:

- **Caption dataset**
  - Prompts/captions designed for educational semantics and ClipArt style consistency.
  - Coverage includes common classroom concepts and activity categories.

- **Image dataset**
  - Curated and categorized image data for ClipArt appearance and robustness.
  - Prioritized clean backgrounds and consistent character depiction.

- **Pose dataset**
  - Pose supervision collected from public pose datasets and synthetically generated samples.
  - Extended coverage to diverse occupations/actions frequently used in educational settings.

## Qualitative Animation Results
The system produces:
- ClipArt-style images aligned with Korean textual descriptions.
- Pose-driven character animations suitable for short educational clips.

Below are pose-driven animation examples generated from **ClipArt characters produced by our system**.

<div class="row">
  <div class="col-md-6 mt-3">
    {% include figure.html path="assets/img/text-to-clipart/penguin.gif" title="Generated ClipArt → pose-driven animation: penguin wearing a cone-shaped hat, jumping." class="img-fluid rounded z-depth-1" %}
    <div class="caption">
      Penguin (generated ClipArt) → pose-driven animation (jumping).
    </div>
  </div>

  <div class="col-md-6 mt-3">
    {% include figure.html path="assets/img/text-to-clipart/boy.gif" title="Generated ClipArt → pose-driven animation: boy wearing a hat, dancing." class="img-fluid rounded z-depth-1" %}
    <div class="caption">
      Boy (generated ClipArt) → pose-driven animation (dancing).
    </div>
  </div>
</div>


## My Role
- Designed the overall pipeline and system integration strategy.
- Performed pose estimation for both **generated** and **existing** character images.
- Implemented the pose-driven animation module that converts estimated poses into character animations.
- Conducted iterative development cycles with stakeholders to improve educational usefulness and deployment readiness.

## Tech Stack
- Diffusion-based text-to-image generation
- Neural machine translation (Korean → English)
- Character pose estimation
- Pose-driven animation / motion transfer
- Deployment: (Gradio / web demo / internal serving)

---

