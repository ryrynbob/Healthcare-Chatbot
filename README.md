# 🩺 Healthcare & Wellness FAQ Chatbot

## 1. Project Overview

This is an interactive conversational agent designed to provide clear, reliable, and non-diagnostic information on common **health and wellness** topics, including nutrition, exercise, and general health definitions.

This project was built for the [MSDS 6393] final submission, fulfilling the requirements for integrating a Hugging Face model and building a Gradio web interface.

**⚠️ Non-Diagnostic Disclaimer:** This chatbot is for informational and educational purposes only. It is **not** a substitute for professional medical advice, diagnosis, or treatment. The chatbot is designed with strict safety fallbacks to refuse any diagnostic or treatment-related queries.

## 2. Key Features

* **Hybrid Q&A:** Answers are primarily retrieved from a curated knowledge base (KB) of 50+ entries for guaranteed accuracy on specific topics.
* **Safety Fallback:** Dialogue logic is implemented to identify and gracefully reject diagnostic or unsafe user inputs.
* **Conversational Generation:** Uses the T5 transformer model to handle general conversational queries and small talk.
* **Semantic Retrieval:** Employs embedding-based search for high-accuracy retrieval from the KB.
* **Gradio Web Interface:** Provides a simple, user-friendly interface accessible via a web browser.

## 3. Architecture & Technical Stack

The chatbot uses a hybrid architecture built around a custom dialogue management system:

1.  **UI:** **Gradio** for the user interface.
2.  **Dialogue Manager:** Custom Python logic in `app.py` detects user intent (Greeting, Safety, FAQ, Chat).
3.  **Retrieval:** **`sentence-transformers/all-MiniLM-L6-v2`** is used to create embeddings for the KB questions. These embeddings are stored in a **FAISS** index for fast, semantic search.
4.  **Generation/Fallback:** **`google/flan-t5-base`** is used for generating human-like responses when a query falls outside the KB.
5.  **Knowledge Base:** **`healthcare_data.json`** (50+ non-diagnostic Q&A entries).

## 4. Installation and Setup

### Prerequisites

You must have Python (3.8+) installed.

### Installation

Clone the repository and install the required libraries:

```bash
# Clone the repository
git clone [https://github.com/ryrynbob/Healthcare-Chatbot.git](https://github.com/ryrynbob/Healthcare-Chatbot.git)
cd Healthcare-Chatbot

# Install all required dependencies
pip install transformers torch gradio sentence-transformers faiss-cpu scikit-learn pandas numpy
