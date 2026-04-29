import os

readme_content = """# 🎥 Stable Video Diffusion - Colab Optimized Studio (v1-stable)

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-ee4c2c)
![License](https://img.shields.io/badge/License-MIT-green)
![Platform](https://img.shields.io/badge/Platform-Google_Colab-orange)

Dieses Repository enthält ein hochgradig optimiertes **Gradio-Studio** zur Generierung von Videos aus Bildern mittels **Stable Video Diffusion (SVD-XT)**. Es wurde speziell für Umgebungen mit begrenztem VRAM (wie die NVIDIA T4 in Google Colab) entwickelt und bietet professionelle Features für die Videoproduktion im Jahr 2026.

---

## ✨ Key Features & Optimierungen

### 🚀 Performance & VRAM Management
* **Model CPU Offloading:** Ermöglicht die Ausführung großer SVD-Modelle auf GPUs mit nur 12GB - 16GB VRAM, indem Teile des Modells bei Nichtgebrauch in den RAM verschoben werden.
* **FP16 Mixed Precision:** Volle Unterstützung für `float16` zur Beschleunigung der Inferenz und Reduzierung des Speicherfußabdrucks.
* **Automated Cache Clearing:** Aggressive Nutzung von `gc.collect()` und `torch.cuda.empty_cache()` nach jedem Batch, um "Out of Memory" (OOM) Fehler zu verhindern.

### 🎬 Erweiterte Videofunktionen
* **SVD-XT Support:** Nutzt das XT-Modell für eine erhöhte Frame-Anzahl (25 Frames) und bessere Bewegungsdynamik.
* **Multi-Scheduler Switching:** Wähle zwischen **Euler Discrete**, **DDIM** und **DPM++**, um das Gleichgewicht zwischen Geschwindigkeit und Qualität anzupassen.
* **Video Looping:** Option zur automatischen Erstellung nahtloser Loops durch Frame-Spiegelung (Ping-Pong-Effekt).
* **Batch Processing:** Generiere mehrere Video-Variationen in einem Durchgang mit automatischer Seed-Inkrementierung.

### 🌐 Konnektivität
* **Ngrok Integration:** Tunneling-Support für einen sicheren externen Zugriff auf das lokal in Colab gehostete Web-Interface.
* **Hugging Face Hub:** Nahtloser Modell-Download über offizielle Repositories mittels Auth-Token.

---

## 🛠️ Installation & Setup

### Voraussetzungen
1. Ein **Hugging Face Token** (mit Schreibzugriff für SVD-Modelle).
2. Ein **Ngrok Authtoken** für den externen Zugriff.

### Schnellstart in Google Colab
Kopiere den Code aus der `svd_studio.py` in eine Colab-Zelle und installiere die Abhängigkeiten:

```bash
pip install -q diffusers transformers accelerate safetensors opencv-python pyngrok gradio imageio
