* RAG search for local document directory

This repo contains a simple script that allows you to ask questions of a local
directory of documents.

> RAG: Retrieval Augmented Generation is a very common use case where we are
> interested in finding information from our data using chat Q&A session. RAG
> methods enable us to use LLM (Large Language Model) on our knowledge base. This
> is much cheaper than training a model from scratch or fine-tuning, and much
> easier to implement.

** Python environment

This script was developed and tested using Python 3.11.6 (3.12.x did not work).
It also assumes a virtual environment (in `.python-version`) named 'vai311'.
Once you've cloned the repo and have an appropriate version of python in a
virtual environment move on to the next step.


** Install requirements

```bash
pip install -r requirements.txt
python rag.py -h   # see the help
```

** Adjust configuration strings in the script

- Adjust the path to your OpenAI credentials
- Check the the data and indices directories exist
- Make some documents available in `./data`

** Create the index (uses OpenAI tokens)

```bash
python rag.py -c "create index"
```

** Start asking questions

```bash
python rag.py "What advice did the caterpillar give to Alice?"
```

