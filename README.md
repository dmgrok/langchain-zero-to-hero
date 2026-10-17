# LangChain and LangGraph Zero to Hero

A hands-on notebook that walks through the core building blocks of LangChain and LangGraph, from a first model call to tool-using agents with memory and human-in-the-loop review. It brings examples from the official LangChain and LangGraph documentation and community material together into one guided path.

> **Versioned educational snapshot.** The notebook was written and run in February 2025 against LangChain 0.3.2 and LangGraph 0.2.60 (exact pins in `requirements.txt`). It is a learning resource, not production code and not a reference for the latest APIs. Several imports and classes it uses, such as `ConversationBufferMemory`, `LLMChain`, `langchain.vectorstores` and the `state_modifier` argument, have since been deprecated or renamed upstream. Check the current [LangChain](https://python.langchain.com/) and [LangGraph](https://langchain-ai.github.io/langgraph/) documentation before reusing these patterns.

## What the notebook covers

- **Models and messages:** basic chat model calls and the OpenAI-compatible message format.
- **Prompts:** prompt templates and few-shot prompting.
- **Chains:** composing prompts, models and output parsers with the pipe operator.
- **Retrieval:** text splitting, document loaders, embeddings, FAISS vector store, retrievers and contextual compression.
- **Memory:** conversation memory with the legacy LangChain approach, then with LangGraph checkpoints.
- **Agents and tools:** custom tools, tool-calling agents, LangGraph ReAct agents, streaming and recursion limits.
- **Human in the loop:** pausing a graph with `interrupt`, asking the user for missing input, web search with Tavily, and reviewing tool calls before they run.

## Prerequisites

- Python 3.11, the version used by the dev container and by the recorded run.
- An [OpenAI API key](https://platform.openai.com/settings/organization/api-keys).
- A [Tavily API key](https://app.tavily.com/) for the web search examples.

Running the notebook calls paid APIs. The notebook uses `gpt-3.5-turbo` and `text-embedding-ada-002` to keep costs low; if those models are no longer available to your account, change the model names in the affected cells.

## Set up the environment

Choose one option.

**Dev container or GitHub Codespaces.** Open the repository in VS Code with the Dev Containers extension, or in a Codespace. The container uses Python 3.11 and installs `requirements.txt` automatically.

**Local virtual environment.**

```bash
git clone https://github.com/dmgrok/langchain-zero-to-hero.git
cd langchain-zero-to-hero
python3.11 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

**Google Colab.** Upload `Quickstart_langchain.ipynb` to Colab. The first cell installs the pinned packages.

## Configure API keys

The notebook's `set_env` helper looks for each key in Colab secrets, then Kaggle secrets, then a local `.env` file.

- **Colab:** add `OPENAI_API_KEY` and `TAVILY_API_KEY` in the Secrets panel.
- **Local or dev container:** copy the sample file and fill in your keys. `.env` is ignored by git.

```bash
cp .env-sample .env
```

## Launch the notebook

- **VS Code:** open `Quickstart_langchain.ipynb` and select the `.venv` or dev container Python interpreter as the kernel.
- **Jupyter in the browser:**

  ```bash
  pip install jupyterlab
  jupyter lab Quickstart_langchain.ipynb
  ```

Run the cells from top to bottom. The first two cells run `pip install` for Colab users; in a prepared environment they only confirm that the pinned packages are present. Saved outputs have been cleared, so each run produces its own results.

## Credits and acknowledgments

Most examples are adapted from the official LangChain and LangGraph documentation, combined with community examples, to offer one practical learning path.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
