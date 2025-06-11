# 🏭 Factory Access Control System Using NLP and Computer Vision

This project simulates an automated access control system for a factory. The system determines whether a worker can enter a facility based on compliance with safety regulations (PPE: Personal Protective Equipment). It combines **Natural Language Processing (NLP)** and **Computer Vision**, and was developed as part of an academic project.

---

## 📌 Overview

The system operates in two main stages:

### 1. `simulacion.py` – End-to-End Simulation (PDF → Prompt → CESGA)
- Internally uses `modulo_pln.py` to process a non-standardized PDF describing safety policies.
- Extracts required PPEs using the **OpenAI GPT API**, and generates a structured `JSON` file.
- Lets the user select a factory area and an image simulating a camera capture.
- Generates an English prompt based on the selected area's PPEs.
- Uploads both the prompt and image to the CESGA cluster for remote processing.

### 2. `modulo_vc.py` – Computer Vision Analysis
- Loads and runs the **Qwen2-VL-7B-Instruct** model.
- Analyzes the image and checks whether the worker is wearing the required PPEs.
- Outputs a result text indicating access is **granted** or **denied** based on detection.

> ⚠️ The vision model is large and is executed remotely on FinisTerrae III at CESGA.

---

## ⚙️ Requirements

Install all required Python packages using:

```bash
pip install -r requirements.txt
```
---
## 🚀 How to Run

> This project is modular and each script can be run independently. Here’s the typical usage flow:

### 1. Extract PPE requirements from a PDF and simulate camera and generate prompt
```bash
python simulacion.py
```
- A file dialog will prompt you to select a PDF.
- It generates a `normativas.json` file containing all structured EPI data.
- Choose an area from the JSON.
- Select an image (e.g., of a worker).
- The script will:
  - Generate a prompt based on the PPEs for that area.
  - Upload the image and prompt to the CESGA cluster.
  - Automatically launch a remote job.

### 2. Run the vision model and generate decision
```bash
python modulo_vc.py
```
- This analyzes the image using the Qwen2-VL-7B-Instruct model.
- Outputs a decision and a log in `respuesta.txt`.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 👤 Author

**Roque de Arcos, Breixo Brea, Samuel Gutierrez**  
AI Engineering Students  
University of Santiago de Compostela  

> This project is part of my personal portfolio to demonstrate applied skills in NLP, Computer Vision, prompt engineering, and distributed computing.
