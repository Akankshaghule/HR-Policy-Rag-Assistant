# 🤖 HR Policy RAG Assistant

An AI-powered **Human Resources (HR) Policy Assistant** that allows users to ask questions about HR policies in natural language and receive relevant, AI-generated answers.

This project uses **Retrieval-Augmented Generation (RAG)** to connect a Large Language Model (LLM) with information retrieved from HR policy documents. Instead of relying only on the model's general knowledge, the system uses relevant document context to help generate more useful, policy-focused responses.

## 📸 Application Output

The following screenshot shows the output of the HR Policy RAG Assistant.

![HR Policy RAG Assistant Output](docs/output.png)

## 🎯 Project Objective

HR policy documents often contain information about leave, attendance, employee benefits, workplace rules, and other organizational procedures. Finding a specific answer manually can take time.

The objective of this project is to build an interactive AI assistant that makes HR policy information easier to access through natural-language questions.

### Problem Statement

Traditional document searching often requires users to know which document or section contains the information they need. A RAG-based assistant can retrieve relevant content based on the meaning of a question and use that content to generate a contextual answer.

### Proposed Solution

The HR Policy RAG Assistant combines document retrieval with an LLM-based response-generation process. Users enter a question through a Streamlit interface, and the application processes the question through the assistant pipeline to produce a response.

## ✨ Key Features

- **Natural-Language Question Answering:** Ask HR-related questions using everyday language.
- **Retrieval-Augmented Generation:** Combines document retrieval with AI-generated responses.
- **Semantic Search:** Uses vector embeddings to identify relevant information based on meaning.
- **Document-Based Context:** Uses retrieved information to guide response generation.
- **Interactive Chat Interface:** Provides a simple interface built with Streamlit.
- **Conversation History:** Displays previous questions and answers during the current session.
- **Modular Python Code:** Separates the user interface and assistant logic into different modules.
- **Evaluation Support:** Includes an `evaluate.py` script for project evaluation.

## 🧠 What Is Retrieval-Augmented Generation (RAG)?

Retrieval-Augmented Generation is an AI approach that combines information retrieval with text generation.

A traditional LLM generates responses from the knowledge learned during training and the context provided in its prompt. A RAG system retrieves relevant information from an external knowledge source before generating a response.

This helps the model answer questions using information specific to a particular document collection.

### How RAG Works in This Project

1. **Document Preparation:** HR policy information is prepared for processing.
2. **Text Chunking:** Large documents are divided into smaller text segments so relevant information can be retrieved efficiently.
3. **Embedding Generation:** Text segments are converted into numerical vectors that represent their semantic meaning.
4. **Vector Storage:** The vectors are stored in a searchable vector index.
5. **User Query:** The user enters a question through the Streamlit application.
6. **Retrieval:** The system searches for relevant information using the question.
7. **Context and Prompt Construction:** Retrieved information is supplied to the language model as context.
8. **Answer Generation:** The LLM generates a response based on the supplied context and instructions.
9. **Response Display:** The generated answer is displayed in the chat interface.

## 🏗️ System Architecture

The project follows a modular architecture in which the interface communicates with the HR assistant pipeline.

```text
             ┌──────────────────────┐
             │         User         │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │   Streamlit UI       │
             │       app.py         │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │ HR Assistant Pipeline│
             │   Query Processing   │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │ Document Retrieval   │
             │   Vector Search      │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │ Relevant HR Context  │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │   LLM Response       │
             │     Generation       │
             └──────────┬───────────┘
                        │
                        ▼
             ┌──────────────────────┐
             │   Answer in Chat     │
             └──────────────────────┘
```

*Note: This diagram represents the conceptual RAG workflow. The precise retrieval, orchestration, and model configuration are defined in the implementation.*

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Streamlit | Interactive web interface |
| LangChain | Components for building LLM and retrieval workflows |
| LangChain Community | Community integrations |
| LangChain Text Splitters | Splitting documents into smaller text chunks |
| FAISS CPU | Vector similarity search |
| Groq integration | Access to supported LLMs through LangChain |
| python-dotenv | Loading configuration from environment variables |
| Jupyter Notebook | Experimentation and development |

## 📂 Project Structure

```text
HR-Policy-Rag-Assistant/
│
├── data/                    # Project data and source documents
│
├── docs/
│   └── output.png           # Application screenshot
│
├── hr_assistant/
│   ├── ...                  # Assistant and RAG modules
│
├── app.py                   # Streamlit application
├── main.py                  # Main project entry point
├── evaluate.py              # Evaluation script
├── rag.ipynb                # RAG experimentation notebook
├── requirements.txt         # Python dependencies
├── .gitignore               # Files excluded from Git
└── README.md                # Project documentation
```

## ⚙️ Installation and Setup

Follow these steps to run the project locally.

### Prerequisites

- Python installed on your system
- Git
- A Groq API key if required by your current configuration

### 1. Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/Akankshaghule/HR-Policy-Rag-Assistant.git
cd HR-Policy-Rag-Assistant
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure Environment Variables

If the assistant requires a Groq API key, create a `.env` file in the project root and add the variable name expected by your application.

For example:

```env
GROQ_API_KEY=your_groq_api_key
```

Replace the placeholder with your own API key. Check the configuration code to confirm the exact variable name expected by the application.

**Security:** Never commit your `.env` file or expose API keys in your source code or screenshots.

### 5. Run the Application

Start the Streamlit interface:

```bash
streamlit run app.py
```

Streamlit will display a local URL in the terminal. Open that URL in your browser to use the application.

## 💬 Example Questions

You can test the assistant with questions such as:

- How many annual leave days are available to employees?
- What is the company's sick leave policy?
- What are the rules for working remotely?
- What is the procedure for requesting leave?
- What employee benefits are described in the policy?

The responses depend on the documents available to the system and the configuration of the language model.

*These are example questions, not claims about the specific policies included in the project.*

## 🔍 Understanding the Main Components

### 1. Streamlit Interface — `app.py`

The application provides the user interface. It displays the title, accepts questions through a chat input, shows previous messages, and displays the assistant's responses.

### 2. HR Assistant Module — `hr_assistant/`

This package contains the assistant's underlying logic, including the pipeline used by the interface. Its internal modules are responsible for implementing the configured retrieval and response-generation workflow.

### 3. RAG Notebook — `rag.ipynb`

The notebook provides a place to experiment with and understand the retrieval-augmented generation workflow.

### 4. Evaluation Script — `evaluate.py`

This script supports evaluation of the assistant. The actual evaluation criteria and results should be taken from the implementation and recorded test outputs.

### 5. Main Script — `main.py`

This file provides an additional project entry point. Refer to its implementation for its specific execution behavior.

## ⚠️ Limitations

- Response quality depends on the relevance and completeness of the available HR documents.
- Incorrect, outdated, or incomplete source documents may lead to misleading answers.
- LLM-generated responses may contain errors, so important policy decisions should be verified against official documents.
- The application should not be treated as a replacement for authorized HR guidance.
- Performance depends on the selected language model, embedding configuration, retrieval settings, and available computing resources.

## 🚀 Future Improvements

- Support uploading additional HR policy documents.
- Display retrieved document excerpts alongside answers.
- Provide source references for easier answer verification.
- Improve retrieval quality through chunk-size and similarity-search tuning.
- Add automated tests and a documented evaluation dataset.
- Improve error handling for missing documents and API failures.
- Add persistent conversation history if required.
- Deploy the application for access through a hosted interface.

## 🎓 Learning Outcomes

Through this project, I explored:

- The fundamentals of Retrieval-Augmented Generation.
- Document chunking and embedding concepts.
- Vector similarity search using FAISS.
- LLM integration with a Python application.
- Building an interactive AI application with Streamlit.
- Organizing an AI project into modular components.
- Managing dependencies and configuration for a Python project.

## 👩‍💻 Author

**Akanksha Ghule**

GitHub: [@Akankshaghule](https://github.com/Akankshaghule)

## 📄 License

No license is specified in this README. If you intend to make the project reusable by others, consider adding an appropriate open-source license.

---

*Built to explore how Retrieval-Augmented Generation can make HR policy information easier to access through natural-language interaction.*
