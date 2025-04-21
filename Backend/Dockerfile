FROM --platform=linux/amd64 python:3.9-slim-buster

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libffi-dev \
    libssl-dev \
    libmupdf-dev \
    git \
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements file
COPY requirements.txt .

# Install pip packages in smaller groups with increased timeouts
# Group 1: Core dependencies (smaller packages)
RUN pip install --no-cache-dir --timeout=300 \
    fastapi \
    uvicorn \
    pydantic \
    python-dotenv \
    requests \
    python-multipart \
    numpy \
    Pillow \
    boto3

# Group 2: PyMuPDF (medium-sized)
RUN pip install --no-cache-dir --timeout=300 PyMuPDF

# Group 3: Vector DBs and embeddings
RUN pip install --no-cache-dir --timeout=300 \
    chromadb \
    pinecone

# Group 4: OpenAI client
RUN pip install --no-cache-dir --timeout=300 openai

# Group 5: Mistral
RUN pip install --no-cache-dir --timeout=300 mistralai

# Group 6: Install docling
RUN pip install --no-cache-dir --timeout=300 docling

# Group 7: Install sentence-transformers (instead of downloading torch first)
RUN pip install --no-cache-dir --timeout=600 sentence-transformers --no-deps
RUN pip install --no-cache-dir --timeout=600 torch==1.11.0 --index-url https://download.pytorch.org/whl/cpu

# Group 8: GitHub package (with its dependencies resolved)
RUN pip install --no-cache-dir --timeout=300 git+https://github.com/brandonstarxel/chunking_evaluation.git

# Copy application code
COPY . .

# Expose port 8000
EXPOSE 8000

# Environment variable for PORT (Cloud Run requires this)
ENV PORT=8000

# Run FastAPI with Uvicorn
CMD ["sh", "-c", "uvicorn main:app --host 0.0.0.0 --port ${PORT}"]