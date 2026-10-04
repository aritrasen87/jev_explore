# Jev Explore

This repository is a small sandbox for experimenting with Jev-based ranking and LangChain integrations. It includes notebooks and utilities for:

- Jev basics and classifier usage
- LangChain TypeSafe flows
- Reranking with `jev-reranker`
- BM25 / relevance comparison examples

## Project structure

- `01_jev_basics.ipynb` – introductory Jev examples
- `02_jev_langchain.ipynb` – LangChain + TypeSafe + reranker examples
- `main.py` – minimal script entry point
- `pyproject.toml` – project dependencies and Python version
- `.venv/` – local virtual environment created by `uv`

## Prerequisites

- Python 3.13
- `uv` installed on your machine
- An API key for OpenRouter or another supported Typesafe backend

## 1) Create and activate the virtual environment

From the repo root:

```bash
cd /Users/aritrasen/Documents/code/github/jev_explore
uv venv --python 3.13
source .venv/bin/activate
```

If you are using VS Code, select the interpreter from `.venv/bin/python` after the environment is created.

## 2) Install dependencies

Use `uv` to install the project dependencies from `pyproject.toml`:

```bash
uv sync
```

This will install packages such as:

- `jev-reranker`
- `langchain-community`
- `langchain-typesafe`
- `rank-bm25`

If you want to add a package manually later, use:

```bash
uv add <package-name>
```

## 3) Configure environment variables

Create a `.env` file in the project root:

```env
OPEN_ROUTER_API_KEY=your_openrouter_api_key_here
TYPESAFE_API_KEY=your_openrouter_api_key_here
TYPESAFE_BASE_URL=https://openrouter.ai/api
```

The notebooks call `load_dotenv()` and read these values automatically. The reranker cells also use `TYPESAFE_API_KEY` / `TYPESAFE_BASE_URL` directly.

## 4) Run the project


### Jupyter notebooks

Open the notebook files in VS Code or Jupyter and make sure the kernel points to the project virtual environment.

If notebook support is not available yet:

```bash
uv pip install jupyter ipykernel
python -m ipykernel install --user --name jev-explore
```

Then open the notebook and select the `jev-explore` kernel.

## 5) Typical workflow

1. Activate the environment
2. Confirm your `.env` values are set
3. Run the notebook cells in order


## 6) Troubleshooting

### Missing API key error

If you see:

```text
ConfigurationError: Set TYPESAFE_API_KEY or pass api_key to use Jev.
```

Then make sure either:

- your `.env` file contains `TYPESAFE_API_KEY`, or
- you pass `api_key=` explicitly when creating `JevReranker`

### Environment not selected in VS Code

Use the Python: Select Interpreter command and choose the environment under:

```text
/Users/aritrasen/Documents/code/github/jev_explore/.venv/bin/python
```

## Notes

This project is designed as a learning and prototyping repo. The dependencies are intentionally minimal, and the notebooks are the main place for experimentation.
