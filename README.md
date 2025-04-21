# Automated-RAG-Pipeline-for-Financial-Document-Insights

## Project Summary
This project delivers an automated Retrieval-Augmented Generation (RAG) pipeline designed to efficiently extract and analyze insights from NVIDIA's quarterly financial reports. By integrating advanced PDF parsing, flexible chunking strategies, and vector databases (Pinecone, ChromaDB), this system provides accurate, fast, and scalable document retrieval and query responses. Users interact seamlessly through a Streamlit frontend connected to FastAPI-powered backend and Airflow-managed workflows.


## Technologies Used:
- **Frontend**: Streamlit  
- **Backend & APIs**: FastAPI  
- **Workflow Automation**: Apache Airflow  
- **Vector Databases**: Pinecone, ChromaDB  
- **Document Parsing**: PyMuPDF, Docling, Mistral OCR  
- **LLM Integration**: OpenAI (via LiteLLM)  
- **Cloud Storage**: AWS S3  
- **Deployment & Containerization**: Docker  
- **Languages**: Python

## Key Features:
- **Customizable PDF Parsing & Chunking**: Flexible selection of parsing methods (Mistral OCR, PyMuPDF, Docling) and advanced chunking strategies (section-based, table-based, sliding window)
- **Hybrid Search Retrieval**: Optimized retrieval using vector embeddings
- **Automated Workflow**:  End-to-end automation with Airflow for ETL processes
- **Dynamic LLM-Generated Responses**: Precise and insightful query responses
- **Interactive User Interface**: Intuitive Streamlit dashboard allowing easy parameter experimentation
- **Efficient Data Management**: Scalable storage and fast retrieval using AWS S3, Pinecone, and ChromaDB
