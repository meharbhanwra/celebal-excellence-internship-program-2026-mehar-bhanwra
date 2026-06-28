# Agentic AI Routing Agent

A simple Agentic AI project that demonstrates how an intelligent agent can route user requests to the appropriate tool based on the user's intent.

This project was developed as part of the **Celebal Technologies AI Internship – Week 8** assignment to introduce the fundamentals of agentic workflows and tool orchestration.

---

## Project Overview

The application implements a lightweight AI agent capable of analyzing a user's query and selecting the appropriate tool to execute.

Instead of solving every task itself, the agent acts as a **decision-maker**, routing requests to specialized tools and returning structured responses.

Currently, the agent supports:

* **Calculator Tool** – Evaluates mathematical expressions.
* **Keyword Extraction Tool** – Extracts important keywords from input text.
* **Word Counter Tool** – Counts the number of words in a given sentence (bonus feature).

---

## Agent Workflow

```text
                User Query
                     │
                     ▼
              Routing Agent
                     │
      ┌──────────────┼──────────────┐
      │              │              │
      ▼              ▼              ▼
 Calculator   Keyword Extractor   Word Counter
      │              │              │
      └──────────────┼──────────────┘
                     ▼
           Structured JSON Response
```

The routing agent determines the user's intent using simple rule-based logic and dispatches the request to the appropriate tool.

---

## Features

* Intelligent routing based on user intent
* Modular tool architecture
* Structured JSON responses
* Error handling for invalid inputs
* Interactive command-line interface
* Easy to extend with additional tools

---

## Tools

### Calculator Tool

Evaluates mathematical expressions entered by the user.

**Example**

**Input**

```
Calculate 45 + 15 * 2
```

**Output**

```json
{
    "type": "calculator",
    "input": "45 + 15 * 2",
    "result": "75"
}
```

---

### Keyword Extraction Tool

Extracts up to five meaningful keywords from a sentence after removing common stopwords and punctuation.

**Example**

**Input**

```
Extract keywords from Artificial Intelligence is transforming healthcare and education.
```

**Output**

```json
{
    "type": "keyword_extractor",
    "input": "Artificial Intelligence is transforming healthcare and education.",
    "result": [
        "artificial",
        "intelligence",
        "transforming",
        "healthcare",
        "education"
    ]
}
```

---

### Word Counter Tool (Bonus)

Counts the total number of words in the provided text.

**Example**

**Input**

```
Count words Artificial Intelligence is transforming healthcare and education.
```

**Output**

```json
{
    "type": "word_counter",
    "input": "Artificial Intelligence is transforming healthcare and education.",
    "result": 7
}
```

---

## Technologies Used

* Python
* Regular Expressions (`re`)
* Basic Agent Routing Logic
* JSON-style Structured Responses

---

## Project Structure

```
├── agent.ipynb
├── README.md
```

---

## Future Improvements

Possible extensions include:

* Sentiment Analysis Tool
* Language Translation Tool
* Text Summarization Tool
* Weather Information Tool
* Calculator using safe expression parsing instead of `eval()`
* LLM-based intent detection using LangChain or Hugging Face models

---

## Learning Outcomes

Through this project, the following concepts were explored:

* Agent-based task routing
* Tool orchestration
* Intent detection
* Modular software design
* Structured API-style responses
* Exception handling and input validation

---

## Getting Started

### Prerequisites

* Python 3.9 or later
* Jupyter Notebook or Google Colab

### Installation

Clone the repository:

```bash
git clone https://github.com/meharbhanwra/celebal-excellence-internship-program-2026-mehar-bhanwra.git
cd celebal-excellence-internship-program-2026-mehar-bhanwra/week-8
```

No additional libraries are required. The project uses only Python's standard library (`re`).

### Running the Project

1. Open the Jupyter Notebook (`agent.ipynb`).
2. Run all notebook cells sequentially.
3. Execute the sample test cases provided in the notebook.
4. Optionally, use the interactive query loop to test your own inputs.

### Example Queries

**Calculator**

```text
Calculate 20 + 5
```

**Keyword Extraction**

```text
Extract keywords from Artificial Intelligence is transforming industries.
```

**Word Counter**

```text
Count words Machine learning is changing the future of healthcare.
```

**Unsupported Query**

```text
Tell me a joke.
```

The agent returns a structured JSON response indicating the selected tool and its output.

## Author

**Mehar Bhanwra**
B.Tech Computer Science & Engineering

Celebal Technologies AI Internship – Week 8
