---
layout: page
title: COMPASS
description: A RAG-based tool that identifies and maps the prerequisite concepts needed to understand scientific papers.
img: assets/img/COMPASS/logo_COMPASS.png
importance: 1
category: fun
related_publications: false
---

<div class="row justify-content-sm-center">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid
      path="assets/img/COMPASS/logo_COMPASS.png"
      class="img-fluid rounded z-depth-1"
    %}
  </div>
</div>

## Overview

**COMPASS** (_Concept Oriented Mapping of Prerequisites for Academic Scientific Sensemaking_) is a RAG-based tool designed to help readers understand difficult scientific papers.

Instead of directly explaining a complex passage, COMPASS identifies the **prerequisite concepts** required to understand it and organizes them into a personalized learning map.

The main idea is simple: **give the map, not the answer**.

[View the project on GitHub](https://github.com/LeBengouz/COMPASS)

## How it works

The user provides:

- a scientific paper in PDF format,
- a description of their existing knowledge,
- and a passage they are struggling to understand.

COMPASS parses the document, retrieves relevant context using both the structure of the paper and semantic similarity, and asks an LLM to identify the concepts that should be understood beforehand.

These concepts are then organized as a **directed prerequisite graph**, while concepts already covered by the user's background are excluded.

<div class="row justify-content-sm-center">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid
      path="assets/img/COMPASS/learning_map_Attention.png"
      title="Example of a COMPASS prerequisite learning map on Attention is all you need"
      class="img-fluid rounded z-depth-1"
    %}
  </div>
</div>

For each prerequisite, COMPASS provides:

- a short explanation of why it is needed,
- its dependencies on other concepts,
- suggested search queries,
- and a checkpoint question to verify understanding.

## Pipeline

`PDF → PyMuPDF4LLM → Sentence Transformers → FAISS → Hierarchical Retrieval → LLM → Prerequisite DAG → Graphviz`

The retrieval stage combines local context, section-level context and semantic similarity to preserve both the structure and meaning of the original paper.

## Technologies

- Python
- Retrieval-Augmented Generation (RAG)
- Sentence Transformers
- FAISS
- PyMuPDF4LLM
- OpenAI API
- Graphviz
- Streamlit

## Current state

The current version supports personalized prerequisite generation for one scientific paper at a time, semantic and section-based retrieval, dependency validation, interactive exploration of concepts and PNG export of the resulting learning map.

The project is primarily an exploration of how **LLMs and information retrieval can assist active learning without replacing the learner's own research and reasoning process**.
