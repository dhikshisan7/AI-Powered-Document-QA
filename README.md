# AI-Powered Document Q&A Assistant

An AI-powered application that allows users to ask questions about PDF documents and receive answers based on the document's content. The project uses Retrieval-Augmented Generation (RAG) to retrieve relevant text passages before generating an answer with a Large Language Model (LLM).

## Project Overview

Searching lengthy documents manually can be time-consuming. This project simplifies document analysis by allowing users to upload a PDF, ask questions in natural language, and receive relevant answers with source page references.

The system is designed to use information retrieved from the uploaded document rather than relying solely on the model's general knowledge.

## Features

- **PDF text extraction:** Extracts selectable text from uploaded PDF files.
- **Text chunking:** Divides extracted text into smaller sections for retrieval.
- **Text embeddings:** Converts document chunks into numerical representations using Sentence Transformers.
- **Semantic retrieval:** Uses FAISS to find relevant document chunks for a question.
- **AI-generated answers:** Uses an LLM through the Groq API to generate answers from retrieved context.
- **Source page references:** Displays the page numbers associated with retrieved text.
- **Missing-information handling:** Instructs the assistant to report when the available document excerpts do not contain enough information.
- **Interactive interface:** Provides a question box and an Ask Document button using ipywidgets.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Google Colab | Development and execution environment |
| PyMuPDF | PDF text extraction |
| Sentence Transformers | Text embedding generation |
| FAISS | Similarity search and retrieval |
| Groq API | LLM-based answer generation |
| ipywidgets | Interactive notebook interface |

## How It Works

1. **Upload a PDF:** The user uploads a document through the notebook.
2. **Extract text:** The application extracts text and retains page numbers.
3. **Create chunks:** The text is divided into smaller, overlapping sections.
4. **Generate embeddings:** Sentence Transformers converts the chunks into embeddings.
5. **Index the chunks:** FAISS stores the embeddings for similarity search.
6. **Retrieve relevant content:** The user's question is embedded and compared with the indexed chunks.
7. **Generate an answer:** The retrieved excerpts and question are sent to the LLM through the Groq API.
8. **Display the result:** The interface displays the generated answer and the source pages associated with the retrieved passages.

## System Architecture

PDF Upload → Text Extraction → Chunking → Embedding Generation → FAISS Index → Relevant Chunk Retrieval → LLM Answer Generation → Answer and Source Pages

## Getting Started

### Prerequisites

- A Google account to use Google Colab.
- A Groq API key.
- A text-based PDF for testing.

### Installation

Open the notebook in Google Colab and install the required packages:

```python
%pip install -q groq pymupdf sentence-transformers faiss-cpu ipywidgets
```

### Configuration

1. Obtain an API key from the Groq Console: https://console.groq.com/
2. Enter the key securely when prompted by the notebook.
3. Do not hardcode your API key or upload it to GitHub.
4. Run the notebook cells in order.
5. Upload a PDF when prompted.
6. Wait for text extraction, embedding generation, and indexing to complete.
7. Enter a question in the interface and click **Ask Document**.

Use the exact model ID configured in the notebook. API model availability and usage limits may change.

## Example

**Question:** What skills are mentioned in this document?

**Example answer:** The assistant identifies technical skills, tools and platforms, data and AI skills, and soft skills from the uploaded document.

**Source:** Page 1.

The actual answer depends on the PDF provided.

## Testing

The application should be tested with:

- Questions whose answers are explicitly present in the document.
- Questions that require combining information from relevant passages.
- Questions whose answers are not present in the document.
- Different PDFs containing multiple pages.

For unsupported questions, the application is instructed to state that it could not find enough information in the uploaded document. This behavior should be evaluated with different test questions; it is not a guarantee that every generated answer will be correct.

## Limitations

- Text extraction may not work on scanned PDFs without OCR.
- Retrieval quality depends on chunk size, embeddings, and the content of the document.
- The LLM may still produce inaccurate answers despite grounding instructions.
- Source page references identify retrieved passages and do not independently prove that every claim in an answer is correct.
- API availability, rate limits, and model access depend on the provider.
- The current interface runs in a notebook and is not a standalone deployed web application.

## Future Improvements

- Add OCR support for scanned PDFs.
- Support multiple PDF files in one session.
- Improve retrieval and evaluate answer accuracy.
- Display the relevant source excerpts alongside answers.
- Add a standalone web interface using Streamlit.
- Add automated tests and a broader evaluation dataset.

## Security and Privacy

Never commit API keys, private documents, personal resumes, or other sensitive information to a public repository. Use environment variables or secure notebook inputs for credentials.

## Author

Developed as a Generative AI and Prompt Engineering internship project.

## License

Add a license if you intend to publish and permit reuse of the project. Otherwise, you may leave this section out until you choose a license.
