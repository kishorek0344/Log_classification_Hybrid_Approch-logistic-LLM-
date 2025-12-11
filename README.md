# Log Classification With Hybrid Classification Framework (Logistic Classification + LLM)

A flexible and scalable log-classification system that integrates Regex rules, ML-based classifiers, and LLM inference to handle both predictable and complex log patterns. This hybrid approach ensures robust performance when dealing with structured logs, semi-structured logs, or logs with limited labeled training data.

---

## Classification Approaches

1. **Regular Expression (Regex)**:
   - Fast and deterministic.
   - Ideal for simple and predictable log formats.

2. **Sentence Transformer + Logistic Regression**:
   - Handles complex log patterns when sufficient labeled training data is available.
   - Generates sentence embeddings using a Sentence Transformer model and classifies them using a Logistic Regression layer.

3. **LLM (Large Language Models)**:
   - Acts as a fallback for highly complex or insufficiently labeled log types.
   - Complements Regex and ML-based classifiers for improved reliability.

---

## Folder Structure

1. **`training/`**  
   - Contains training scripts for Sentence Transformer and Logistic Regression models.  
   - Includes code for regex-based classification logic.

2. **`models/`**  
   - Stores trained model files, including Sentence Transformer embeddings and the Logistic Regression model.

3. **`resources/`**  
   - Contains sample CSV files, output files, images, and other supporting resources.

4. **Root Directory**  
   - Contains the FastAPI server implementation (`server.py`).

---

## Setup Instructions

1. **Install Dependencies**  
   Make sure Python is installed. Then install the necessary packages:

   ```bash
   pip install -r requirements.txt
   ```

2. **Run the FastAPI Server**:
   To start the server, use the following command:

   ```bash
   uvicorn server:app --reload
   ```

   Once the server is running, you can access the API at:
   - `http://127.0.0.1:8000/` (Main endpoint)
   - `http://127.0.0.1:8000/docs` (Interactive Swagger documentation)
   - `http://127.0.0.1:8000/redoc` (Alternative API documentation)

---

## Usage

Upload a CSV file containing logs to the FastAPI endpoint for classification. Ensure the file has the following columns:
- `source`
- `log_message`

The output will be a CSV file with an additional column `target_label`, which represents the classified label for each log entry.

---
