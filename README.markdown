# README - Text Retrieval and Generation System

## Project Overview
This project implements a text retrieval and generation system powered by AI, designed to extract information from PDF documents and answer user queries based on the content. The system leverages the following techniques:
- **Text Extraction**: Extracts text from PDF files using the `pymupdf` library.
- **Text Chunking**: Splits text into smaller chunks with a specified size and overlap for processing.
- **Text Embedding**: Generates embeddings for text chunks using the `all-MiniLM-L6-v2` model from the `sentence-transformers` library.
- **Similarity Search**: Uses the `faiss` library to perform similarity search and retrieve relevant text chunks based on user queries.
- **Text Generation**: Employs the `gpt2` model from the `transformers` library to generate answers to user questions using the retrieved context.

## Installation
To set up the project, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install dependencies**:
   Ensure you have Python 3.11 or later installed. Then, install the required packages:
   ```bash
   pip install pymupdf sentence-transformers faiss-cpu transformers
   ```

3. **Download required files**:
   - Ensure the `news.pdf` file (or your target PDF) is available in the project directory.
   - The notebook automatically downloads model weights for `all-MiniLM-L6-v2` and `gpt2` during execution.

## Usage
1. **Run the Jupyter Notebook**:
   Launch the `text_generation.ipynb` notebook using Jupyter:
   ```bash
   jupyter notebook text_generation.ipynb
   ```

2. **Steps in the Notebook**:
   - **Text Extraction**: The notebook reads text from `news.pdf` using the `read_pdf` function.
   - **Chunking**: The `chunk_by_char` function splits the text into chunks of 300 words with a 50-word overlap.
   - **Embedding**: The `all-MiniLM-L6-v2` model generates embeddings for the chunks.
   - **Indexing**: FAISS creates an index for similarity search using the embeddings.
   - **Query Processing**: A sample query (`what is the artifical inteligens ?`) is encoded, and the top 3 most similar chunks are retrieved.
   - **Answer Generation**: The GPT-2 model generates an answer based on the retrieved chunks.

3. **Example Query**:
   ```python
   query = 'what is the artificial intelligence ?'
   ```
   The system retrieves relevant chunks and generates an answer using GPT-2. Example output:
   ```
   Answer: Artificial intelligence is currently in its infancy. It can be applied to a wide range of topics including: robotics, artificial intelligence, medical and medical technology, healthcare, and information technology...
   ```

## Project Structure
- `text_generation.ipynb`: The main Jupyter notebook containing the code for text extraction, processing, and generation.
- `news.pdf`: The input PDF file containing the text to be processed (ensure it exists or replace with your own PDF).
- **Dependencies**:
  - `pymupdf`: For PDF text extraction.
  - `sentence-transformers`: For generating text embeddings.
  - `faiss-cpu`: For efficient similarity search.
  - `transformers`: For text generation with GPT-2.

## Notes
- The system assumes the `news.pdf` file contains relevant text, such as the provided context about Artificial Intelligence.
- The `all-MiniLM-L6-v2` model is lightweight and efficient for embedding generation.
- The GPT-2 model is used for text generation, but you can replace it with other models from the `transformers` library for better performance.
- FAISS is configured to use `IndexFlatL2` for simplicity; you can explore other index types for larger datasets.
- Ensure sufficient computational resources, as embedding generation and text generation can be resource-intensive.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

## License
This project is licensed under the MIT License.