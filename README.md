# Agentic RAG run locally

## Setup

1. Create virtual environment:
```bash
python -m venv myvenv
```

2. Activate virtual environment:
```bash
# Windows
myvenv\Scripts\activate
# MacOS
source venv\bin\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Configure `.env`:
### Using Ollama (Local Inference)
```env
USE_HUGGINGFACE=no
HUGGINGFACE_API_TOKEN=
REASONING_MODEL_ID=deepseek-r1:7b-8k
TOOL_MODEL_ID=qwen2.5:14b-instruct-8k
```

5. Setting up Ollama Models:
### 1. Install ollama (https://ollama.ai)

### 2. Pull the base models:
```bash
ollama pull deepseek-r1:7b
ollama pull qwen2.5:14b-instruct-q4_K_M
```

### 3. Create custom models with extended context windows:
```bash
# Create Deepseek model with 8k context - recommended for reasoning
ollama create deepseek-r1:7b-8k -f ollama_models/Deepseek-r1-7b-8k

# Create Qwen model with 8k context - recommended for conversation
ollama create qwen2.5:14b-instruct-8k -f ollama_models/Qwen-14b-Instruct-8k

# On MacOS you might need to use -from instead of -f

# Create Deepseek model with 8k context - recommended for reasoning
ollama create deepseek-r1:7b-8k -from ollama_models/Deepseek-r1-7b-8k

# Create Qwen model with 8k context - recommended for conversation
ollama create qwen2.5:14b-instruct-8k -from ollama_models/Qwen-14b-Instruct-8k
```

6. Create directory to store pdf:
```bash
mkdir data
# Copy your PDFs into the data directory
```

6. Ingest PDFs:
```bash
python ingest_pdfs.py
```

7. Run RAG application:
```bash
python r1_smolagent_rag.py
```
