
# GPT-2 Text Generation Web App

This is a simple web application built with **FastAPI** to generate text using a fine-tuned **GPT-2** model.  
It uses an adapter-based fine-tuning (via PEFT - Parameter-Efficient Fine-Tuning) and serves a user-friendly frontend to interact with the model.

---

## 📁 Project Structure

```
gpt2-webapp/
├── app/
│   ├── __init__.py
│   ├── main.py          # FastAPI application routes
│   ├── models.py        # GPT-2 model loading and text generation logic
│   ├── static/          # Static files (e.g., CSS)
│   │   └── styles.css
│   └── templates/       # HTML templates (Jinja2)
│       └── index.html
├── assets/              # Additional resources (optional)
│   ├── dir.txt
│   ├── run.txt
│   └── sampleinput.txt
├── gpt2-finetuned/      # Fine-tuned GPT-2 model files
│   ├── adapter_config.json
│   ├── adapter_model.safetensors
│   ├── merges.txt
│   ├── special_tokens_map.json
│   ├── tokenizer_config.json
│   ├── training_args.bin
│   └── vocab.json
├── requirements.txt     # Python dependencies
└── README.md             # Project documentation
```

---

## 🚀 Application Details

### Backend
- **FastAPI** serves both the API endpoints and the HTML frontend.
- **TextGenerator** class handles model loading and text generation using `transformers` and `peft`.
- Model loading includes:
  - **Base Model**: `gpt2`
  - **Fine-tuned Adapter**: Loaded from `gpt2-finetuned/` directory.
- Uses **GPU** (CUDA) if available, otherwise **CPU**.

### Frontend
- **HTML (Jinja2 Templates)** and **CSS** to create a simple and elegant UI.
- Users can input a **prompt** and adjust:
  - `max_length`
  - `temperature`
  - `top_k`
  - `top_p`
- Displays the **generated text** and **processing time** after submission.

---

## 🛠️ Installation & Running Locally

1. **Clone the repository:**
   ```bash
   git clone <repo-url>
   cd gpt2-webapp
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   ```

3. **Activate the environment:**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On Mac/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

5. **Run the app:**
   ```bash
   uvicorn app.main:app --reload
   ```

6. **Visit**:
   Open your browser and go to: [http://localhost:8000](http://localhost:8000)

---

## 📋 Sample Input

> **Science Topic:**
> 
> Quantum computing is an area of computing focused on developing computer technology based on the principles of quantum theory, which explains the nature and behavior of energy and matter on the quantum level. Quantum computers use quantum bits or qubits which can exist in multiple states simultaneously, unlike classical binary bits. This allows quantum computers to process massive amounts of data and solve complex problems much faster than traditional computers. Major companies like IBM, Google, and Microsoft are investing heavily in quantum computing research.

---

## 📦 Key Files

- **app/main.py**: FastAPI app handling routes and request processing.
- **app/models.py**: Model class (`TextGenerator`) for loading GPT-2, PEFT adapter, and generating text.
- **gpt2-finetuned/**: Fine-tuned GPT-2 model and adapter weights.
- **requirements.txt**: All necessary Python libraries for the project.
- **templates/index.html**: Frontend page to enter prompts and view generated outputs.
- **static/styles.css**: Basic CSS for styling the frontend.

---

## ✨ Features

- Easy deployment-ready FastAPI structure.
- Fine-tuned GPT-2 text generation using **low-resource adapters** (PEFT).
- Supports adjusting model inference parameters (length, temperature, top_k, top_p).
- Displays inference time.
- Clean and simple UI for interaction.

---

## 📢 Notes

- Make sure the `gpt2-finetuned` folder is correctly placed in the project root.
- CUDA device is automatically selected if available for faster generation.
- The app is designed for educational and demonstration purposes; you can easily extend it to a production deployment (e.g., using Docker, Render, or Azure).

---
