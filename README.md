# 🏭 Factory Access Control System Using NLP and Computer Vision

This project simulates an automated access control system for a factory. The system determines whether a worker can enter a facility based on compliance with safety regulations (PPE: Personal Protective Equipment). It combines **Natural Language Processing (NLP)** and **Computer Vision**, and was developed as part of an academic project.

---

## Overview

The system operates in three main stages:

### 1. `modulo_pln.py` – NLP for Policy Extraction
- Reads a non-standardized PDF document describing safety policies.
- Uses the **OpenAI GPT API** to extract PPE requirements for areas and tasks.
- Outputs the structured data in a `JSON` format.

### 2. `simulacion.py` – Camera Simulation + Prompt Generation
- Simulates a camera by allowing the user to manually select an image.
- Lets the user choose a work area, then extracts the required PPEs from the JSON.
- Automatically generates an English-language prompt and uploads the image and prompt to a **remote cluster** at CESGA (Supercomputing Center of Galicia).

### 3. `modulo_vc.py` – Computer Vision Analysis
- Loads and runs the **Qwen2-VL-7B-Instruct** model.
- Analyzes the image and checks whether the worker is wearing the required PPEs.
- Outputs a result text indicating access is **granted** or **denied** based on detection.

---

## ⚙️ Requirements

Install all required Python packages using:

```bash
pip install -r requirements.txt
