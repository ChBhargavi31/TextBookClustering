# TextBookClustering
-PDF Document Clustering Web Application

A Flask-based web application that automatically categorizes PDF documents into thematic clusters using Natural Language Processing (NLP) and Latent Dirichlet Allocation (LDA) topic modeling.

Overview
This project was developed during an Industrial Data Science internship at DATAi2i Pvt Ltd. The application accepts a PDF document upload, extracts and preprocesses its text content, applies a pre-trained LDA model to identify the dominant topic, and returns the thematic cluster the document belongs to. Users can also browse and filter the existing document database by keyword.

Features

Upload any PDF and get its topic cluster predicted in real time
Pre-trained LDA model with 13 topic categories (e.g., digital, statistics, javascript, node, memory, energy)
Full NLP pipeline: text extraction → cleaning → tokenization → stopword removal → corpus vectorization → topic inference
Keyword-based filtering to browse documents by topic frequency
Web interface built with Flask and Jinja2 templates


Tech Stack

LayerToolsWeb FrameworkFlaskData HandlingPandasPDF ExtractionPyPDF2Text CleaningdataprepNLP / TokenizationNLTKTopic ModelingGensim (LDA)VectorizationGensim Corpora (Bag-of-Words)Model PersistencePickle

Project Structure

├── app.py                  # Main Flask application
├── venv/
│   ├── data.pkl            # Pre-processed document dataset
│   ├── model.pkl           # Pre-trained LDA model
│   └── topic_mapping.pkl   # Topic ID to label mapping
├── templates/
│   ├── index.html          # Home page with document list and upload form
│   ├── result.html         # Cluster result page after PDF upload
│   └── pdfs.html           # Keyword-filtered document browser


How It Works

Text Extraction — PyPDF2 reads up to 25 pages from the uploaded PDF
Text Cleaning — dataprep cleans raw text; NLTK tokenizes and removes stopwords and domain-specific common words
Corpus Building — Gensim converts cleaned tokens to a Bag-of-Words corpus using a pre-built dictionary
Topic Inference — The pre-trained LDA model assigns topic probabilities; the dominant topic is selected
Cluster Mapping — The topic ID is mapped to a human-readable label (e.g., "digital", "statistics", "javascript")
Result Display — The predicted cluster and related documents are rendered on the results page



Setup and Installation

bash# Clone the repository
git clone https://github.com/ChBhargavi31/<repo-name>.git
cd <repo-name>

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install flask pandas PyPDF2 nltk gensim dataprep scikit-learn

# Download NLTK data
python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords')"

# Run the application
python app.py

Visit http://127.0.0.1:5000 in your browser.


Usage


Home page — View all pre-clustered documents and upload a new PDF for classification
Upload — Select a PDF file and click Upload; the app returns its predicted topic cluster
Keyword Search — Navigate to /pdfs?keyword=<topic> to filter documents by a specific topic keyword



Topic Categories

The LDA model identifies 13 topic clusters including:

security · motors · digital · statistics · winding · javascript · html · memory · node · performance · energy · angularjs


Dataset

The training dataset consists of 100+ PDF textbooks and technical documents across domains including VLSI design, microprocessors, web development, signal processing, statistics, and power systems.


Internship Context

Developed as part of a 7-week Industrial Data Science internship at DATAi2i Pvt Ltd (May–June 2023), contributing to SOTA machine learning product development under minimal supervision.

Institution: Gayatri Vidya Parishad College of Engineering for Women, Dept. of ECE
University: JNTUK, Kakinada
