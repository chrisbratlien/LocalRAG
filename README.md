# LocalRAG - PDF Question Answering System

A Streamlit-based application that enables users to upload PDF documents, ask questions, and receive contextual answers using Local Large Language Models (LLMs) through Ollama. The system uses RAG (Retrieval Augmented Generation) to provide accurate responses based on the document content.

## Features

- PDF document upload and processing
- Document summarization
- Question-answering based on document content
- Chat history tracking
- Vector embeddings using FAISS
- Local LLM integration via Ollama

## Prerequisites

- Python 3.8+
- Ollama installed and running locally
- Required Python packages (listed in requirements.txt)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/vamsid07-LocalRAG.git
cd vamsid07-LocalRAG
```

2. Create and activate a virtual environment (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install the required packages:
```bash
pip install -r requirements.txt
```

4. Ensure Ollama is installed and running with the llama3.1 model:
```bash
ollama pull llama3.1
```

## Project Structure

```
vamsid07-LocalRAG/
├── app.py              # Main Streamlit application
├── requirements.txt    # Python dependencies
└── pdfs/              # Directory for uploaded PDF files
```

## Usage

1. Start the Streamlit application:
```bash
streamlit run app.py
```

2. Access the application through your web browser (typically at `http://localhost:8501`)

3. Upload a PDF document using the sidebar uploader

4. Click "Upload & Embed" to process the document

5. (Optional) Click "Summarize Document" to get a quick overview of the content

6. Ask questions in the text input field and click "Ask" to receive answers

## Features in Detail

### Document Processing
- Uses `PyPDFDirectoryLoader` for PDF processing
- Implements recursive text splitting for optimal chunk size
- Utilizes FAISS for efficient vector storage and retrieval

### Embeddings
- Custom embedding implementation using `SentenceTransformer`
- Uses the 'all-MiniLM-L12-v2' model for document embeddings
- Efficient document chunking with 700-character chunks and 50-character overlap

### Question Answering
- Leverages Ollama's local LLM for inference
- Implements RAG for accurate and contextual responses
- Maintains chat history for reference

## Configuration

The application uses several key parameters that can be modified in `app.py`:

- Chunk size: 700 characters (adjustable)
- Chunk overlap: 50 characters (adjustable)
- Embedding model: 'all-MiniLM-L12-v2'
- Ollama endpoint: "http://localhost:11434"
- Model: "llama3.1"

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

[Add your chosen license here]

## Acknowledgments

- LangChain for the document processing framework
- Ollama for local LLM hosting
- Streamlit for the web interface
- FAISS for vector storage
- Sentence Transformers for embeddings

## Troubleshooting

1. If you encounter memory issues, try:
   - Reducing the chunk size
   - Processing fewer documents at once
   - Using a lighter embedding model

2. If Ollama connection fails:
   - Ensure Ollama is running locally
   - Verify the correct port (11434)
   - Check if the llama3.1 model is properly installed

3. For PDF processing issues:
   - Ensure PDFs are not password-protected
   - Verify PDF file permissions
   - Check the PDFs directory exists and is writable
