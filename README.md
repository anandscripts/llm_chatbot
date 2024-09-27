
# LLM Chatbot

This project implements an LLM-based chatbot that interacts with users by answering queries using information retrieved from a set of PDF documents. The chatbot is built using LangChain, Chroma for vector storage, and Ollama embeddings.

## Project Structure

- **`interface.py`**:  
  This is the user interface for the chatbot, built using Streamlit. It takes user input, queries the model, and displays responses. It also maintains session state to display chat history.

- **`db_storage.py`**:  
  This script handles loading PDF files from the `data` directory, splitting the text into manageable chunks, embedding the chunks using the **Ollama** embedding model, and storing them in a Chroma vector database for efficient retrieval.

- **`query_data.py`**:  
  This script retrieves the most relevant chunks from the Chroma database based on user queries. It uses a Retrieval-Augmented Generation (RAG) approach to select and pass relevant context to the **Ollama LLM** (`llama3.2`), which generates a response.

- **`data/`**:  
  This directory contains the PDF files that the chatbot will reference when generating responses.

- **`requirements.txt`**:  
  This file contains all necessary Python dependencies for the project.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/anandscripts/llm_chatbot.git
   ```

2. Navigate to the project directory:
   ```bash
   cd llm_chatbot
   ```

3. Install the required dependencies by running:
   ```bash
   pip install -r requirements.txt
   ```

## Ollama Models

The chatbot leverages the **Ollama** models for embedding and generating responses. The following models are used in this project:

- **`nomic-embed-text`**: This model is employed to create high-quality embeddings for the text extracted from the PDFs. These embeddings help the chatbot understand the semantic meaning of the text, allowing for accurate context retrieval during user queries.

- **`llama3.2`**: This is the primary language model used to generate responses based on the relevant context retrieved from the vector database. The model offers a balance between performance and response time, making it suitable for real-time interactions with users.

## Usage

1. Place the PDF files that you want to use as the chatbot's knowledge base in the `data/` folder.

2. Run the `db_storage.py` script to load and process the documents, splitting them into chunks and storing them in the Chroma vector database:
   ```bash
   python db_storage.py
   ```

3. Start the chatbot by running the `interface.py` Streamlit app:
   ```bash
   streamlit run interface.py
   ```

4. Interact with the chatbot through the Streamlit interface by typing questions, and the chatbot will generate responses based on the context from the PDF files.

## Contribution

Feel free to use, modify, and distribute this code! If you find it helpful or make improvements, I’d love to hear about it. Contributions and feedback are always welcome.
