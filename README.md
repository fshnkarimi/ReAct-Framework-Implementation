```markdown
# ReAct Framework Implementation

This repository contains an implementation of the "ReAct" framework using OpenAI's GPT-3.5 Turbo model and LangChain, enabling dynamic reasoning and interaction with external information sources.

## Prerequisites

Before running the code, ensure that you have the necessary libraries installed and API keys set up:

- OpenAI API key: Obtain one from the OpenAI platform.
- Serper API key: For external search functionality.

Set these keys as environment variables in your local environment or your Colab notebook, as demonstrated in the code.

## Installation

To set up the required libraries and dependencies, run the following commands:

```bash
!pip install --upgrade openai
!pip install --upgrade langchain
!pip install --upgrade python-dotenv
!pip install google-search-results
```

## Usage

1. Import the necessary libraries:

```python
import os
import openai
from langchain.llms import OpenAI
from langchain.agents import load_tools
from langchain.agents import initialize_agent
from dotenv import load_dotenv
```

2. Set your API keys as environment variables:

```python
os.environ["OPENAI_API_KEY"] = "YOUR_OPENAI_API_KEY"
os.environ["SERPER_API_KEY"] = "YOUR_SERPER_API_KEY"
```

3. Configure the LLM and tools:

```python
llm = OpenAI(model_name="gpt-3.5-turbo", temperature=0)
tools = load_tools(["google-serper", "llm-math"], llm=llm)
agent = initialize_agent(tools, llm, agent="zero-shot-react-description", verbose=True)
```

4. Run the agent with your desired queries:

```python
# Example 1: Query about Ronaldo
agent.run("What is Ronaldo's current team? How much is his salary in this team?")

# Example 2: Query about Gemini in Google
agent.run("What is Gemini in Google?")
```

## Output

The code will execute the queries and provide responses using the ReAct framework, combining reasoning and action to generate informative answers.

## Attribution
This code example was adapted from the [LangChain documentation](https://python.langchain.com/docs/modules/agents/agent_types/react)
, and credit goes to them for the original implementation.
