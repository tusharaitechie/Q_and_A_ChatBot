# 🤖 Enhanced Q&A Chatbot with OpenAI & LangChain

> **An end-to-end Generative AI application that combines OpenAI-powered language models, LangChain, prompt engineering, and Streamlit to deliver an interactive Question & Answer experience.**

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io/)
[![LangChain](https://img.shields.io/badge/Framework-LangChain-1C3C3C?logo=chainlink&logoColor=white)](https://www.langchain.com/)
[![OpenAI](https://img.shields.io/badge/LLM-OpenAI-412991?logo=openai&logoColor=white)](https://openai.com/)
[![License](https://img.shields.io/badge/License-For%20Learning%2FPortfolio-lightgrey)](#license)

---

## 📌 Project Overview

**Enhanced Q&A Chatbot** is a lightweight Generative AI application built with **Python, Streamlit, OpenAI, and LangChain**.

The application allows a user to:

- Enter an OpenAI API key securely through the Streamlit sidebar.
- Select a configured OpenAI model.
- Ask questions using a simple conversational interface.
- Generate natural-language answers using an LLM.
- Control response-related settings through the UI.
- Track LangChain activity through **LangSmith** when tracing is configured.

The project demonstrates the complete flow from **user question → prompt template → LangChain chain → OpenAI LLM → parsed response → Streamlit UI**.

---

## 🎯 Why This Project?

Traditional rule-based Q&A systems depend heavily on predefined questions and answers. They struggle when a user asks the same question using different wording.

This project demonstrates a modern **LLM-based Question & Answer architecture**, where the user's natural-language question is passed to an LLM through a structured prompt.

### Example

**User:**
> What is machine learning?

**Application:**
> Machine learning is a branch of artificial intelligence that enables systems to learn patterns from data and make predictions or decisions without being explicitly programmed for every scenario.

The same architecture can be extended into more advanced AI systems such as:

- RAG-based document assistants
- Customer-support chatbots
- Internal knowledge assistants
- HR assistants
- Technical documentation assistants
- Enterprise AI copilots

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🧠 LLM-Powered Q&A | Uses an OpenAI chat model to generate responses |
| 🔗 LangChain Integration | Uses LangChain to construct the LLM processing chain |
| 📝 Prompt Engineering | Uses `ChatPromptTemplate` to structure model instructions |
| 🖥️ Streamlit UI | Provides a clean interactive web interface |
| 🔐 API Key Input | Allows the API key to be entered as a password field |
| ⚙️ Model Selection | Provides model selection through the sidebar |
| 🎛️ Response Controls | Provides temperature and max-token controls in the UI |
| 📊 LangSmith Tracking | Supports LangChain/LangSmith tracing configuration |
| 📦 Modular Flow | Separates response generation from the UI layer |
| 🚀 Easy to Run | Can be started locally with a single Streamlit command |

---

## 🏗️ Architecture

```text
                    ┌───────────────────────┐
                    │       User            │
                    │   Enters a Question   │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │    Streamlit UI       │
                    │  Question + Settings  │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │   Prompt Template     │
                    │  System + User Input  │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │      LangChain        │
                    │    Processing Chain   │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │     OpenAI LLM        │
                    │  Natural Language Gen │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │   StrOutputParser     │
                    │   Converts to String  │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │   Answer displayed    │
                    │    in Streamlit       │
                    └───────────────────────┘
```

---

## 🔄 How the Application Works

The core processing pipeline is:

```text
User Question
     ↓
ChatPromptTemplate
     ↓
LangChain Chain
     ↓
ChatOpenAI
     ↓
StrOutputParser
     ↓
Generated Answer
     ↓
Streamlit UI
```

### 1. User enters a question

The user enters a question in the Streamlit interface.

### 2. Prompt is created

The application uses `ChatPromptTemplate` with two messages:

- **System message** — instructs the model to respond helpfully.
- **User message** — contains the actual question.

Conceptually:

```text
System:
You are a helpful assistant. Please respond to the user queries.

User:
Question: <user question>
```

### 3. LangChain builds the chain

The project uses LangChain's pipe-style composition:

```python
chain = prompt | llm | output_parser
```

This creates a clean processing pipeline:

```text
Prompt → LLM → Output Parser
```

### 4. OpenAI generates the answer

The question is sent to the configured chat model through `ChatOpenAI`.

### 5. Output is parsed

`StrOutputParser` converts the model response into a usable string.

### 6. Answer is displayed

The generated answer is returned to Streamlit and displayed to the user.

---

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| **Python** | Core programming language |
| **Streamlit** | Interactive web application UI |
| **OpenAI** | Large Language Model provider |
| **LangChain** | LLM application framework and chain orchestration |
| **LangChain OpenAI** | OpenAI integration for LangChain |
| **Prompt Templates** | Structured prompt construction |
| **StrOutputParser** | Converts LLM output into a string |
| **python-dotenv** | Loads environment variables from `.env` |
| **LangSmith** | Optional tracing/observability for LangChain workflows |

---

## 📁 Project Structure

```text
Q_and_A_ChatBot/
│
├── app.py                  # Main Streamlit application
├── requirements.txt        # Python dependencies
├── README.md               # Project documentation
│
└── venv/                   # Local virtual environment
```

### `app.py`

The main application file containing:

- Streamlit interface
- API-key input
- Model selection
- Prompt template
- LangChain chain
- OpenAI integration
- Response generation
- LangSmith configuration

### `requirements.txt`

Contains the libraries required to run the project:

```text
langchain-openai
langchain
python-dotenv
langchain_community
streamlit
```

> **Note:** A local `venv/` directory is normally not required in GitHub. It is recommended to keep virtual environments outside the repository and add `venv/` to `.gitignore`.

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/tusharaitechie/Q_and_A_ChatBot.git
cd Q_and_A_ChatBot
```

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Configure Your OpenAI API Key

The application provides an API-key field directly in the Streamlit sidebar.

For local development, you can also use environment variables.

Create a `.env` file:

```env
OPENAI_API_KEY=your_openai_api_key_here
LANGCHAIN_API_KEY=your_langsmith_api_key_here
```

### ⚠️ Security

**Never commit API keys or secrets to GitHub.**

Make sure `.env` is included in `.gitignore`:

```gitignore
.env
venv/
__pycache__/
*.pyc
```

If a secret is accidentally pushed to GitHub, revoke/rotate it immediately.

---

## 5. Run the Application

Start Streamlit:

```bash
streamlit run app.py
```

The application will normally open at:

```text
http://localhost:8501
```

---

# 🖥️ Using the Application

After launching the application:

### Step 1 — Enter API Key

Use the sidebar to enter your OpenAI API key.

### Step 2 — Select the Model

Choose a model from the configured model-selection dropdown.

### Step 3 — Configure Response Settings

The UI provides controls for:

- Temperature
- Maximum tokens

### Step 4 — Ask a Question

Enter your question in the main input field.

### Step 5 — View the Answer

The application sends the question through the LangChain pipeline and displays the generated answer.

---

# 🔍 Core Implementation

The project demonstrates a simple but important LLM application pattern.

### Prompt Template

```python
prompt = ChatPromptTemplate.from_messages(
    [
        (
            "system",
            "You are a helpful assistant. Please respond to the user queries"
        ),
        (
            "user",
            "Question: {question}"
        )
    ]
)
```

### LLM

```python
llm = ChatOpenAI(model=engine)
```

### Output Parser

```python
output_parser = StrOutputParser()
```

### Chain

```python
chain = prompt | llm | output_parser
```

### Invocation

```python
answer = chain.invoke({"question": question})
```

This is the central concept of the project:

```text
Prompt
  ↓
LLM
  ↓
Output Parser
  ↓
Answer
```

---

# 🧠 Key AI Concepts Demonstrated

This project provides practical exposure to several concepts frequently used in modern Generative AI development.

### 1. Large Language Models (LLMs)

The application uses a chat-based LLM to understand natural-language questions and generate responses.

### 2. Prompt Engineering

Instead of sending raw user input directly, the application structures the request using a system instruction and a user message.

### 3. LangChain Expression Language

The pipeline:

```python
prompt | llm | output_parser
```

demonstrates composable LLM workflows.

### 4. Output Parsing

`StrOutputParser` converts the LLM response into a plain string suitable for displaying in an application.

### 5. Observability

LangSmith configuration is included to support tracing and monitoring of LangChain workflows.

---

# 💡 What This Project Demonstrates to a Recruiter

This project showcases hands-on understanding of:

- Python application development
- Generative AI
- LLM integration
- OpenAI API integration
- LangChain
- Prompt engineering
- LLM chains
- Output parsing
- Streamlit application development
- Environment variable management
- Basic LLM observability with LangSmith
- Building an AI feature end-to-end rather than only experimenting in a notebook

---

# 🧪 Example Questions

You can test the chatbot with questions such as:

```text
What is Artificial Intelligence?
```

```text
Explain machine learning in simple terms.
```

```text
What is the difference between AI and ML?
```

```text
What is Generative AI?
```

```text
Explain Large Language Models.
```

The quality and accuracy of responses depend on the selected model and its configuration.

---

# 🔐 Security Best Practices

For production usage, the following improvements are recommended:

- Never hard-code API keys.
- Never commit `.env` files.
- Rotate exposed credentials immediately.
- Use a secrets manager in production.
- Restrict API-key permissions where possible.
- Add authentication before exposing the application publicly.
- Add rate limiting and usage monitoring.
- Validate and sanitize user inputs where appropriate.

---

# 🚧 Current Scope & Future Enhancements

This repository focuses on a **basic LLM-powered Q&A workflow**. It can be extended into a more production-oriented Generative AI application.

### Planned / Possible Enhancements

- [ ] Conversation history / memory
- [ ] Streaming responses
- [ ] RAG with PDF/document ingestion
- [ ] Embedding generation
- [ ] Vector database integration
- [ ] Semantic search
- [ ] Source/document citations
- [ ] Conversation persistence
- [ ] Authentication and authorization
- [ ] Better error handling
- [ ] API backend using FastAPI
- [ ] Docker containerization
- [ ] Automated testing
- [ ] CI/CD pipeline
- [ ] Production deployment
- [ ] Evaluation framework for LLM responses

### Possible Future Architecture

```text
                 ┌─────────────────┐
                 │     User        │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │   Streamlit /   │
                 │   Web Frontend  │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Query Processing│
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │   Retriever     │
                 │  (Future RAG)   │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Context + Query │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │      LLM        │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Final Response  │
                 └─────────────────┘
```

---

# 📊 Project Highlights

| Area | Implementation |
|---|---|
| Application Type | Generative AI / Q&A Chatbot |
| Language | Python |
| Frontend | Streamlit |
| LLM Framework | LangChain |
| LLM Provider | OpenAI |
| Prompting | ChatPromptTemplate |
| Chain | Prompt → LLM → Parser |
| Output Handling | StrOutputParser |
| Configuration | Environment variables + Streamlit UI |
| Observability | LangSmith configuration |
| Deployment Ready | Suitable foundation for further deployment |

---

# 📚 Learning Outcomes

By building this project, you gain practical experience with:

1. Integrating an LLM into a Python application.
2. Building structured prompts.
3. Creating LangChain pipelines.
4. Calling chat models programmatically.
5. Parsing LLM output.
6. Building an interactive Streamlit interface.
7. Handling API credentials securely.
8. Configuring LangSmith tracing.
9. Designing an extensible Generative AI application.
10. Understanding the foundation required before moving to RAG and advanced AI agents.

---

# 🛠️ Troubleshooting

### `ModuleNotFoundError`

Install the dependencies again:

```bash
pip install -r requirements.txt
```

### Streamlit command not found

Make sure your virtual environment is activated:

```bash
venv\Scripts\activate
```

Then run:

```bash
streamlit run app.py
```

### API authentication error

Check that:

- The API key is valid.
- The correct model is configured.
- Your API account has access to the selected model.
- The key has not been revoked.

### Environment variables are not loading

Verify that:

- `.env` exists in the project root.
- Variable names are correct.
- `python-dotenv` is installed.
- The application is restarted after changing environment variables.

---

# 📌 Important Note

This project is designed as a **learning and portfolio project** demonstrating an end-to-end LLM Q&A application.

It should not be considered a production-ready enterprise chatbot without additional security, monitoring, evaluation, error handling, authentication, cost controls, and deployment hardening.

---

# 👨‍💻 Author

**Tushar**

Software Engineer | AI/ML Enthusiast | Generative AI Developer

GitHub:  
https://github.com/tusharaitechie

---

# ⭐ Support

If you find this project useful for learning Generative AI, feel free to **star the repository** and explore the code.

---

## 📄 License

This project is intended for educational and portfolio purposes. Add an appropriate open-source license to the repository if you plan to distribute or reuse the project publicly.
