# YouTube Content Chatbot — RAG Application

A Retrieval-Augmented Generation (RAG) application that enables users to ask questions about YouTube video content and receive context-aware answers using transcript retrieval, semantic embeddings, FAISS, and Google Gemini.

## Overview

Understanding lengthy YouTube videos can be time-consuming, especially when searching for specific information. This project addresses that problem by transforming video transcripts into searchable context that an LLM can use to answer user queries.

The application combines **LangChain, Hugging Face embeddings, FAISS, and Google Gemini** to retrieve relevant transcript passages and generate answers based on the retrieved information.

## Key Features

- **YouTube Transcript Extraction** — Retrieves available video transcripts.
- **Text Chunking** — Splits transcripts into smaller chunks for effective retrieval.
- **Semantic Embeddings** — Represents transcript chunks as numerical vectors using Hugging Face.
- **Vector Similarity Search** — Uses FAISS to identify relevant transcript passages.
- **Context-Aware Generation** — Supplies retrieved context to Google Gemini to generate answers.
- **Environment-Based Configuration** — Keeps API credentials separate from application code.

## Technology Stack

| Category | Technologies |
|---|---|
| Language | Python |
| LLM Framework | LangChain |
| Transcript Extraction | YouTube Transcript API |
| Embedding Model | Sentence Transformers — `all-MiniLM-L6-v2` |
| Vector Store | FAISS |
| Language Model | Google Gemini |
| Environment Management | python-dotenv |
| Development Environment | Jupyter Notebook |

## Architecture

```text
YouTube Video
     |
     v
Transcript Extraction
     |
     v
Text Chunking
     |
     v
Hugging Face Embeddings
     |
     v
FAISS Vector Store
     |
     v
User Query
     |
     v
Relevant Context Retrieval
     |
     v
Google Gemini + Context
     |
     v
Context-Aware Answer
```

### How It Works

1. **Extract:** Obtain the available transcript for the selected YouTube video.
2. **Split:** Divide the transcript into smaller chunks using `RecursiveCharacterTextSplitter`.
3. **Embed:** Convert chunks into vector representations using a Hugging Face embedding model.
4. **Index:** Store the vectors in FAISS for similarity-based retrieval.
5. **Retrieve:** Find transcript chunks relevant to the user's question.
6. **Generate:** Pass the retrieved context and question to Google Gemini to generate a response.

## Project Structure

```text
YouTube-Content-Chatbot-RAG-Application/
├── rag.ipynb
├── requirements.txt
├── .gitignore
└── .env                  # Local only; not committed
```

## Installation and Setup

### Prerequisites

- Python installed on your system
- Git
- A Google Gemini API key
- Internet connectivity for transcript retrieval and API access

### 1. Clone the Repository

```bash
git clone https://github.com/AyushShrivastava2808/YouTube-Content-Chatbot-RAG-Application.git
cd YouTube-Content-Chatbot-RAG-Application
```

### 2. Create and Activate a Virtual Environment

For Windows PowerShell:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the project root:

```env
GOOGLE_API_KEY=your_google_gemini_api_key
```

Generate your API key through [Google AI Studio](https://aistudio.google.com/apikey).

Keep `.env` private and never commit API keys to GitHub.

### 5. Run the Application

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `rag.ipynb` and execute the notebook cells in order.

## Configuration

The notebook uses the following embedding model:

```python
HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-MiniLM-L6-v2"
)
```

The Google Gemini model is configured in the notebook. Ensure that the selected model is available to your API key and supported by the installed integration.

## Limitations

- Answers depend on the availability and quality of the YouTube transcript.
- Videos without accessible transcripts may not be processed.
- Retrieval quality depends on chunking, embeddings, and similarity search.
- Responses can be incomplete or inaccurate when the retrieved context is insufficient.
- Google Gemini API usage may be subject to quotas and rate limits.

## Key Learnings

- Designing a Retrieval-Augmented Generation pipeline.
- Integrating LangChain with an external LLM.
- Generating semantic embeddings using Hugging Face.
- Implementing vector similarity search with FAISS.
- Extracting and preprocessing unstructured text.
- Managing API credentials through environment variables.

## Author

**Ayush Shrivastava**

[GitHub Profile](https://github.com/AyushShrivastava2808) · [Project Repository](https://github.com/AyushShrivastava2808/YouTube-Content-Chatbot-RAG-Application)

---

*Developed to explore practical applications of Retrieval-Augmented Generation, semantic search, and large language models.*
