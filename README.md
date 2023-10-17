# RAG search for local document directory

This repo contains a simple script that allows you to ask questions of a local
directory of documents.

> RAG: Retrieval Augmented Generation is a widespread use case where we are
> interested in finding information from our data using chat Q&A sessions. RAG
> methods enable us to use a LLM (Large Language Model) on our knowledge base. This
> is much cheaper than training a model from scratch or fine-tuning, and much
> easier to implement.

## Python environment

This script was developed and tested using Python 3.11.6 (3.12.x did not work).
It also assumes a virtual environment (in `.python-version`) named 'vai311'.
Once you've cloned the repo and have an appropriate python version in a
virtual environment, move on to the next step. I recommend `pyenv` for this
but tastes may vary.

## Install requirements

```bash
pip install -r requirements.txt
python rag.py -h   # see the help
```

## Adjust configuration strings in the script

- Adjust the path to your OpenAI credentials
- Check that the `data` and `indices` directories exist
- Make some documents available in the `data` directory (it may be a tree)

## Create the index
Here the documents are split up (chunked) and sent to OpenAI a piece at a time
to create the index in a local vector store.  In this case, the vector store is
just a collection of JSON files.

```bash
python rag.py -c "create index"
```

## Start asking questions
When you ask a question, it's compared to the local vector store to find the nearest
matches. Those are sent with the query to OpenAI to formulate the answer.

```bash
python rag.py "What advice did the caterpillar give to Alice?"
```

