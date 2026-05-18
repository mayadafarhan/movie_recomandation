🎬 Movie Recommendation RAG Chatbot

An AI-powered Movie Recommendation Chatbot built using LangChain, ChromaDB, Hugging Face Embeddings, and Qwen LLM.

This project uses Retrieval-Augmented Generation (RAG) to answer movie-related questions intelligently using a custom movie catalog stored in JSON format.

The chatbot can:

Recommend movies by genre
Answer questions about specific movies
Retrieve movie details semantically
Provide ratings, descriptions, directors, and cast information
🚀 Features
Load movie catalog from JSON
Convert movie data into LangChain Documents
Semantic movie search using embeddings
Persistent ChromaDB vector database
AI-generated responses using Qwen LLM
Genre-based recommendations
Interactive chatbot terminal interface
Source document transparency
🛠️ Tech Stack
Python
LangChain
ChromaDB
Hugging Face Transformers
Sentence Transformers
Qwen2.5 Instruct Model
📂 Project Structure
project/
│
├── movies.json              # Movie catalog dataset
├── app.py                   # Main chatbot application
├── chroma_movies_db/        # Persisted Chroma vector database
├── requirements.txt         # Project dependencies
└── README.md                # Documentation
📦 Installation
1. Clone Repository
git clone https://github.com/your-username/movie-rag-chatbot.git
cd movie-rag-chatbot
2. Create Virtual Environment
Windows
python -m venv venv
venv\Scripts\activate
Linux / Mac
python3 -m venv venv
source venv/bin/activate
3. Install Dependencies
pip install -r requirements.txt

Or manually:

pip install langchain langchain-community langchain-chroma langchain-huggingface chromadb sentence-transformers transformers accelerate
📄 Example movies.json
{
  "Sci-Fi": [
    {
      "title": "Inception",
      "year": 2010,
      "director": "Christopher Nolan",
      "cast": ["Leonardo DiCaprio", "Joseph Gordon-Levitt"],
      "description": "A thief enters dreams to steal secrets.",
      "rating": 8.8,
      "duration_min": 148,
      "language": "English"
    }
  ],
  "Drama": [
    {
      "title": "The Shawshank Redemption",
      "year": 1994,
      "director": "Frank Darabont",
      "cast": ["Tim Robbins", "Morgan Freeman"],
      "description": "Two imprisoned men bond over years.",
      "rating": 9.3,
      "duration_min": 142,
      "language": "English"
    }
  ]
}
▶️ Run the Application
python app.py
💬 Example Queries
What sci-fi movies do you have?

Recommend a psychological thriller with a twist ending

Tell me about Inception

Who directed The Shawshank Redemption?

What are the highest rated drama movies?
🧠 How the System Works
1. Load Movie Catalog

The chatbot reads movie data from:

movies.json
2. Create LangChain Documents

Each movie is converted into a structured document.

Example:

Document(
    page_content="""
Genre: Sci-Fi
Title: Inception (2010)
Director: Christopher Nolan
Description: A thief enters dreams to steal secrets.
IMDb Rating: 8.8/10
"""
)
3. Generate Embeddings

Using Hugging Face sentence transformers:

sentence-transformers/all-MiniLM-L6-v2

This converts movie descriptions into semantic vectors.

4. Store Vectors in ChromaDB

The vector database is stored locally in:

./chroma_movies_db
5. Semantic Retrieval

The retriever finds the most relevant movies using similarity search.

retriever = vectorstore.as_retriever(
    search_type="similarity",
    search_kwargs={"k": 10}
)
6. Generate AI Response

The retrieved movie context is sent to the Qwen language model for answer generation.

🤖 Models Used
Embedding Model
sentence-transformers/all-MiniLM-L6-v2
Language Model
Qwen/Qwen2.5-0.5B-Instruct
📌 Prompt Engineering

The assistant uses a custom prompt template to ensure grounded responses.

You are a knowledgeable movie expert assistant.
Use ONLY the movie catalog context below to answer the question.
🔍 Retrieval Features

The chatbot supports:

Genre-based search
Semantic recommendation
Specific movie lookup
Similar movie discovery
Context-aware responses
📈 Future Improvements
Add Streamlit or Gradio web UI
Add hybrid search (BM25 + Vector Search)
Add multilingual movie support
Integrate TMDB API
Add movie posters
Add user watchlists
Docker deployment
Recommendation ranking system
🧪 Sample Output
Ask about the menu: recommend a psychological thriller

Bot:
You may enjoy:
- Inception (2010) — IMDb 8.8
  A mind-bending sci-fi thriller directed by Christopher Nolan.
⚠️ Notes
First run may take time because models download automatically.
ChromaDB is recreated each time the script runs.
Larger models can improve recommendation quality.
❤️ Built With
LangChain
ChromaDB
Hugging Face
Sentence Transformers
Qwen Models
📜 License

This project is licensed under the MIT License.

👩‍💻 Author

Developed by Amira Mohamed 🚀
