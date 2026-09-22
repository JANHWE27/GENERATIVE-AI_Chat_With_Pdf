# GEN AI - Chat With Your PDF

A chatbot-like application built with **AWS Amazon Bedrock**, **Docker**, **Python**, **LangChain**, and **Streamlit**.

It uses Retrieval-Augmented Generation (RAG) to fetch relevant context from your PDF knowledge base and pass it to a Large Language Model along with the user's query, generating accurate, context-aware responses.

## Tech Stack

- **Amazon Bedrock** — foundation models for embeddings and text generation
- **LangChain** — RAG pipeline and retrieval logic
- **FAISS** — vector similarity search
- **Amazon S3** — vector index storage
- **Streamlit** — chat interface
- **Docker** — containerized deployment
- **Python** — application logic

## How It Works

1. PDFs are uploaded and split into chunks
2. Each chunk is converted into a vector embedding
3. Embeddings are stored in a FAISS vector index
4. On a user query, the app retrieves the most relevant chunks from the index
5. The query + retrieved context are sent to the LLM via a prompt template
6. The generated response is displayed to the user

## Run Locally

```bash
docker build -t chat-with-pdf .
docker run -e BUCKET_NAME=<YOUR_S3_BUCKET_NAME> \
  -v ~/.aws:/root/.aws \
  -p 8501:8501 \
  -it chat-with-pdf
```

Open the app at `http://localhost:8501`.
