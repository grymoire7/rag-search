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

## Collect some documents
We now need to make some documents available. First, pick name for this set.
Say, "mydocs". Then add your docs to the `./data/mydocs` directory. This may be
a tree of documents or even a symlink to docs.  In the next step, your index will
be created in the `./indices/mydocs` directory.

## Create the index
Here the documents are split up (chunked) and sent to OpenAI a piece at a time
to create the index in a local vector store.  In this case, the vector store is
just a collection of JSON files.

```bash
python rag.py -c <index_name>
```

Continuing with the previsous example, the command would be `python rag.py -c mydocs` and
the index would be created in the `./indices/mydocs` directory.

## Start asking questions
When you ask a question, it's compared to the local vector store to find the nearest
matches. Those are sent with the query to OpenAI to formulate the answer.

```
python rag.py <data_set_name> # in our example: pythone rag.py mydocs

> Ask your question here
See your response appear here

> quit  # Ask another question or quit
```

## References
This idea is based on the workflow described in [this post](https://paragshah.medium.com/unlock-the-power-of-your-knowledge-base-with-openai-gpt-apis-db9a1138cac4)
and others though the code is now fairly different.  It makes heavy use of the [llama-index](https://github.com/run-llama/llama_index) library.

