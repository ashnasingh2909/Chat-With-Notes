# Chat with Notes

**Chat with Notes** is an AI-powered document assistant that allows users to upload documents and interact with their content through a conversational interface.

The application combines **Streamlit, LangChain, Cohere, and FAISS** to provide document-based question answering using a Retrieval-Augmented Generation (RAG) approach.

## Features

* Upload and process documents
* Ask questions about uploaded files
* AI-powered answers using Cohere
* Semantic document search
* FAISS vector similarity search
* Retrieval-Augmented Generation (RAG)
* Automatic text extraction and chunking
* Interactive chat interface
* Multiple chat sessions
* Suggested questions
* Basic login and sign-up functionality
* Support for multiple document formats

## How It Works

The application processes documents through the following pipeline:

```text
Upload Document
      ↓
Extract Text
      ↓
Split Text into Chunks
      ↓
Generate Embeddings
      ↓
Store Vectors in FAISS
      ↓
Ask a Question
      ↓
Find Relevant Content
      ↓
Send Context to Cohere
      ↓
Generate Answer
```

When a document is uploaded, its text is extracted and divided into smaller chunks. Each chunk is converted into a vector representation using Cohere embeddings and stored in a FAISS index.

When a user asks a question, the application searches the vector database for the most relevant sections of the document. These sections are then provided to the Cohere language model to generate a contextual answer.

## Technology Stack

| Technology    | Purpose                     |
| ------------- | --------------------------- |
| Python        | Application development     |
| Streamlit     | User interface              |
| LangChain     | RAG and document processing |
| Cohere        | Embeddings and AI responses |
| FAISS         | Vector similarity search    |
| PyMuPDF       | PDF text extraction         |
| python-docx   | Word document processing    |
| python-pptx   | PowerPoint processing       |
| pandas        | Data processing             |
| openpyxl      | Excel file processing       |
| python-dotenv | Environment configuration   |

## Project Structure

```text
Chat-With-Notes/
│
├── app.py
├── auth.py
├── qa_chain.py
├── vectorstore.py
├── utils.py
│
├── check_connection.py
├── debug_output.py
├── debug_test.py
├── minimal_test.py
├── simple_test.py
├── test_api.py
├── test_cohere.py
│
├── config.yaml
├── requirements.txt
├── .env
└── README.md
```

### Main Components

**app.py**
Contains the main Streamlit application and user interface.

**auth.py**
Provides the login and registration interface.

**qa_chain.py**
Handles the question-answering process using retrieved document content.

**vectorstore.py**
Creates embeddings and manages the FAISS vector store.

**utils.py**
Handles document extraction, processing, and text splitting.

**requirements.txt**
Contains the dependencies required to run the application.

## Installation

### Clone the Repository

```bash
git clone <your-repository-url>
cd Chat-With-Notes
```

### Create a Virtual Environment

For Windows:

```bash
python -m venv venv
venv\Scripts\activate
```

For macOS/Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

## API Configuration

The application requires a **Cohere API key**.

Create a `.env` file in the project directory:

```env
COHERE_API_KEY=your_cohere_api_key_here
```

Replace `your_cohere_api_key_here` with your actual API key.

> **Important:** Never commit your `.env` file or expose your API key publicly.

## Running the Application

Start the Streamlit application with:

```bash
streamlit run app.py
```

After running the command, open the local Streamlit URL in your browser:

```text
http://localhost:8501
```

## Usage

1. Open the application.
2. Log in or create an account.
3. Upload a supported document.
4. Wait for the document to be processed.
5. Enter a question in the chat box.
6. View the AI-generated response.
7. Ask follow-up questions about the same document.
8. Start a new chat when needed.

## Example Questions

```text
What is the main topic of this document?

Summarize the important points.

What are the key findings?

Explain this concept in simple words.

What are the advantages and disadvantages?

What conclusion does the document provide?

What evidence is mentioned?

Compare the concepts discussed in the document.
```

## Supported File Formats

The application supports the following document types:

* PDF (`.pdf`)
* Microsoft Word (`.docx`)
* PowerPoint (`.pptx`, `.ppt`)
* Excel (`.xlsx`, `.xls`)

> The upload interface may list `.txt`, but TXT extraction is not currently implemented in `utils.py`.

## Document Processing

The application uses text chunking before generating embeddings.

Current configuration:

| Setting          |           Value |
| ---------------- | --------------: |
| Chunk Size       | 1000 characters |
| Chunk Overlap    |  200 characters |
| Retrieved Chunks |               5 |

The chunks are converted into embeddings and stored in FAISS.

When a question is submitted, the application performs a similarity search to locate the most relevant chunks before generating the final response.

## Retrieval-Augmented Generation

**Chat with Notes** uses a RAG architecture.

The process consists of two major stages:

### Retrieval

Relevant information is retrieved from the uploaded document using vector similarity search.

### Generation

The retrieved information is provided to the Cohere language model, which generates a natural-language response.

This allows the application to answer questions based on the user's uploaded content.

## Authentication

The project contains a basic authentication system for demonstration purposes.

The current implementation is not intended for production environments.

For production use, authentication should be replaced with a secure solution that provides:

* Password hashing
* Database-backed users
* Secure sessions
* Authorization
* Secret management

## Testing

The project includes several scripts for testing and debugging.

Examples:

```bash
python check_connection.py
python test_api.py
python test_cohere.py
python simple_test.py
python minimal_test.py
```

These scripts can be used to verify API connectivity and troubleshoot different parts of the application.

## Limitations

* Requires an active Cohere API key.
* Processing large documents can take additional time.
* Vector storage is not configured as a persistent production database.
* Authentication is intended for demonstration purposes.
* Scanned PDFs may require OCR.
* TXT file support requires additional implementation.
* Answer quality depends on the information retrieved from the document.

## Security Recommendations

Before deploying the project publicly:

* Keep API keys in environment variables.
* Add `.env` to `.gitignore`.
* Use secure password hashing.
* Add file validation.
* Set upload size limits.
* Use HTTPS.
* Add API rate limiting.
* Avoid storing sensitive document content in logs.
* Keep different users' documents isolated.

## Future Improvements

* [ ] Add TXT file support
* [ ] Add OCR for scanned documents
* [ ] Support multiple documents at once
* [ ] Add persistent chat history
* [ ] Add document management
* [ ] Add source citations
* [ ] Add streaming responses
* [ ] Add persistent vector storage
* [ ] Improve authentication
* [ ] Add database integration
* [ ] Add document preview
* [ ] Deploy to the cloud

## Contributing

Contributions are welcome.

Create a feature branch:

```bash
git checkout -b feature/your-feature
```

After making your changes:

```bash
git add .
git commit -m "Add your feature"
git push origin feature/your-feature
```

Then create a pull request.

## License

No specific license is currently included with the project.

If the project is published publicly, an appropriate open-source license should be added.

## Project Goal

The goal of **Chat with Notes** is to make document analysis easier and faster by combining AI with semantic document search.

Users can upload their notes or documents and interact with them naturally through questions instead of manually searching through every page.

**Upload → Ask → Retrieve → Understand.**
