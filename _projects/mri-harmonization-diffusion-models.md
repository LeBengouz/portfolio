---
layout: page
title: MRI Harmonization with Diffusion Models
description: Research internship project exploring conditional diffusion models for multi-site MRI harmonization.
img: assets/img/projects/MRI_harmonization/exemple_harmo.png
importance: 1
category: work
related_publications: false
---

**Python · PyTorch · Diffusers · Medical Imaging · Conditional Diffusion Models · MR-CLIP · DIST-CLIP**

[View source code on GitHub](https://github.com/LeBengouz/MRI_Harmonisation_Diffusion_models)

## Project Overview

This project was developed during my **End-of-studies research internship at LIIFE – CHU Lille** and focuses on the harmonization of MRI scans acquired across different sites.

Combining data from multiple hospitals or scanners is valuable for medical research and AI training since it improves statistical power. However, differences in earth's magnetic field, acquisition protocols and equipment can introduce unwanted variability. Thus, the goal of this project was to investigate how to use **conditional diffusion models** in order to reduce these site-related differences while preserving the anatomical information specific to each subject.

**Warning**: All MRI scans presented here are sourced from public datasets.

## Approach

The pipeline uses a **2D conditional diffusion model** trained to reconstruct MRI scans while being guided by both anatomical information and acquisition-site information.

The workflow included:

- extracting 2D slices from MRI volumes,
- generating anatomical representations,
- conditioning the diffusion model on the MRI image and anatomical guidance,
- using site embeddings to control acquisition-related style,
- reconstructing harmonized MRI scans.

Two anatomical guidance strategies were explored:

- **Canny edge maps**,
- representations extracted from a pre-trained **DIST-CLIP** encoder.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/MRI_harmonization/mon_super_model.png" title="Architecture of the 3D diffusion model guided by an embedding and an anatomical representation." class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
Architecture of the 3D diffusion model guided by an embedding and an anatomical representation.
</div>

The project also investigated the integration of **MR-CLIP** representations for acquisition-site conditioning.

## Research Contribution

A key part of the work consisted in evaluating whether representations learned by medical foundation models could improve the conditioning of the diffusion model.

On the one hand, using a deep learning-based anatomical encoder produced a better separation between anatomical information and acquisition style. On the other hand, this improvement did **not directly translate into better harmonization performance**, contrary to the literature's affirmations.

This result provided a key insight and guided further work.

## Engineering & Experimentation

Beyond model training, the project involved building and adapting a complete research pipeline for medical imaging experiments.

Experiments were controlled through configuration files with an easy to use pipeline.

The implementation was developed mainly with **PyTorch and Hugging Face Diffusers**. For the preprocessing, other libraries have been used such as **NiBabel, OpenCV, scikit-image and Albumentations**.

## Key Takeaways

This internship gave me hands-on experience with **diffusion models, medical imaging, and research-oriented deep learning**. It taught me how to design and build an end-to-end project by myself. Moreover, it taught me how to evaluate, compare, and critically interpret results.
