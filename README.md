# 🔎 Semantic Search Engine

A Python-based Semantic Search Engine that retrieves and ranks documents according to their relevance to a user's query. This project demonstrates a TF-IDF lexical-search baseline and an optional embedding-based semantic search implementation using Sentence-Transformers.

## 🚀 Features

- Search a collection of documents using user queries.
- Rank documents using cosine similarity.
- Implement a TF-IDF lexical-search baseline.
- Optionally use dense text embeddings for semantic retrieval.
- Display top-k results with similarity scores and metadata.
- Evaluate retrieval quality using Recall@k.
- Save a local search index and document collection.
- Run without an external API key.

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- TF-IDF Vectorization
- Cosine Similarity
- Sentence-Transformers (optional)
- Text Embeddings
- Information Retrieval

## 📁 Project Structure

```text
semantic-search-engine/
│
├── semantic_search_engine.ipynb
├── README.md
├── requirements.txt
│
└── semantic_search_outputs/
    ├── tfidf_index.pkl
    └── documents.json
```

The output directory is generated when you execute the relevant notebook cells.

## ⚙️ Installation and Setup

### Option 1: Google Colab

1. Download `semantic_search_engine.ipynb`.
2. Open Google Colab.
3. Select **File → Upload notebook**.
4. Upload the notebook.
5. Run the cells sequentially.

The notebook includes a dependency-installation cell.

### Option 2: Run Locally

Clone the repository:

```bash
git clone https://github.com/<your-username>/semantic-search-engine.git
```

Navigate to the project directory:

```bash
cd semantic-search-engine
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate the environment on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open `semantic_search_engine.ipynb` and run the cells in order.

## 🧠 How It Works

### Step 1: Document Collection

Load documents containing identifiers, titles, categories, and text.

### Step 2: Text Vectorization

Convert the document text into numerical vectors using TF-IDF.

### Step 3: Query Processing

Convert the user's query into a vector using the same fitted vectorizer.

### Step 4: Similarity Calculation

Calculate cosine similarity between the query vector and document vectors.

### Step 5: Ranking

Sort documents by similarity score and return the top-k results.

### Step 6: Semantic Embeddings (Optional)

Use Sentence-Transformers to generate dense embeddings for queries and documents. This can improve retrieval when a query uses wording different from the document.

### Step 7: Evaluation

Use a small, manually labelled dataset to demonstrate Recall@k.

## 💻 Example Usage

```python
query = "How can I improve the security of my login?"

results = lexical_search(query, top_k=5)

print(results[["id", "title", "category", "score"]])
```

The results contain document identifiers, titles, categories, text, and similarity scores.

## 🔬 Optional: Embedding-Based Semantic Search

The notebook contains optional code using:

`sentence-transformers/all-MiniLM-L6-v2`

Install the package:

```bash
pip install sentence-transformers
```

Then uncomment the optional embedding-search code cell and execute it.

The model downloads the first time, so an internet connection is required.

**Note:** TF-IDF is a lexical baseline. The embedding-based implementation is the part that explores semantic similarity. Neither approach guarantees that retrieved documents are factually correct.

## 📊 Evaluation

The notebook demonstrates Recall@3 using a small manually labelled query set.

| Metric | Purpose |
|---|---|
| Recall@k | Measures whether relevant documents appear in the top-k results. |
| Mean Reciprocal Rank (MRR) | Measures how highly the first relevant result is ranked. |
| Normalized Discounted Cumulative Gain (nDCG) | Evaluates ranking quality using relevance and result position. |

Only Recall@k is implemented in the starter notebook. MRR and nDCG are potential extensions.

The sample evaluation set is too small to establish real-world search quality.

## ⚠️ Limitations

- The document collection is small and synthetic.
- TF-IDF relies on lexical overlap rather than deep semantic understanding.
- Embedding-based search requires an additional package and model download.
- Search quality depends on document preprocessing, the embedding model, and the evaluation dataset.
- The local pickle index should only be loaded from trusted sources.

## 🔮 Future Improvements

1. Implement hybrid lexical and semantic search.
2. Add a cross-encoder reranking model.
3. Integrate a vector database.
4. Support PDF, DOCX, and other document formats.
5. Add metadata filters and document access controls.
6. Build a Streamlit user interface.
7. Develop a FastAPI search endpoint.
8. Evaluate with larger datasets using Recall@k, MRR, and nDCG.
9. Add document updates and incremental indexing.

## 📜 License

Choose an appropriate open-source license, such as MIT, and add a `LICENSE` file before publishing.
