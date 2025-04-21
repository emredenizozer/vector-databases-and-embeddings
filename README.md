# Document QA with OpenAI Embeddings & ChromaDB

This project demonstrates how to build a document question-answering (QA) system using **OpenAI's embedding and chat models** alongside **ChromaDB**, a persistent vector database.

It allows you to:

- Load .txt documents from a directory

- Split them into chunks

- Generate vector embeddings using OpenAI

- Store them in ChromaDB

- Query the database and generate concise answers using GPT


## 📦 Features
- 🔍 Semantic search over document chunks

- 🧬 Text embeddings powered by OpenAI (text-embedding-3-small)

- 🧠 QA with GPT (gpt-3.5-turbo)

- 💾 Persistent vector storage via ChromaDB

- 🧪 Modular functions for loading, embedding, querying, and responding



## 🛠 Setup

### 1. Clone the repository

```bash
git clone https://github.com/emredenizozer/vector-databases-and-embeddings
cd vector-databases-and-embeddings
```

### 2. Install dependencies

Make sure you’re using Python 3.9+ and create a virtual environment if needed:

```bash
pip3 install -r requirements.txt
```

### 3. Set up your ```.env``` file

```env
OPENAI_API_KEY=your_openai_key_here
```

## 📂 Directory Structure

```bash
.
├── data/
│   └── new_articles/               # Place your .txt documents here
├── db/
│   └── chroma_persistent_storage/  # ChromaDB vector store (auto-created)
├── vector_db_llm.py                # The main application logic
└── .env                            # OpenAI API key

```


## 🚀 Usage

### 🔁 First-time Setup (Uncomment Setup Block)

In main.py, uncomment the **initial setup** block to:

- Load and chunk documents

- Generate and store embeddings in ChromaDB

Run the script:

```bash
python3 vector_db_llm.py
```

After first run, comment the setup block to avoid reprocessing documents.

### ❓ Asking Questions

Once setup is complete, just run the script again to perform semantic queries like:

```python
question = "give me a brief overview of the articles. Be concise, please."
```

The system will:

1. Embed the query

2. Retrieve relevant chunks from ChromaDB

3. Generate a concise answer using GPT-3.5


## 🧩 Functions Breakdown

Function | Purpose
| ------------- | ------------- |
<code>load_documents_from_directory()</code> | Loads .txt files from a folder
<code>split_text()</code>  | Splits text into overlapping chunks
<code>get_openai_embedding()</code>  | Calls OpenAI's API to generate embeddings
<code>query_documents()</code>  | Retrieves relevant document chunks from Chroma
<code>generate_response()</code>  | Constructs a prompt and queries GPT for the answer


## 📌 Notes

- **Only** <code>.txt</code> **files** are supported currently.

- Ideal for summarizing or querying large text corpora.

- Embeddings are cached persistently with ChromaDB.

- Make sure not to overload the OpenAI API quota if you're processing many documents.


## 🧠 Example Output

```txt
==== Answer ====
The articles cover recent developments in AI, including OpenAI's new model, government regulations on AI, and industry applications. They highlight both progress and concerns. Overall, the tone is cautiously optimistic.
```