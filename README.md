# Simple Langchain wrapper 


This project is basically an abstraction of langchain and llm projects so you can achieve the same objective with a single line of code


## Key features:

- Loads documents from a directory
- Splits documents into smaller chunks
- Indexes chunks by embedding vectors for semantic search
- Uses Pinecone vector database for efficient retrieval
- Retrieves most similar chunks to a question  
- Passes similar chunks to Langchain QA model to get answer
- Provides authentication and connectivity validation

## Usage:

1. Instantiate the class with directory and other params

2. Call auth_wrapper() classmethod to validate API keys 

3. Call get_answer() with your question to get the answer

4. Answers are generated by searching over embedded document chunks
   and running a QA model on the most similar chunks to the question
   

```python

langchain_docs_wrapper.env_auth_variables()
langchain_docs_wrapper.auth_wrapper()

wrapper = langchain_docs_wrapper(
    directory=directory,

)


query = "what is xxxxxxx "
answer = wrapper.get_answer(query)

```

## Auth: 

- Set OpenAI_API_KEY, pinecone_api_key, pinecone_environment,pinecone_index_name  as environment variables

```bash
export pinecone_api_key='1492xxxxxxxx'
export pinecone_environment='us-xxxx'
export pinecone_index_name='xxxxx'
```

- auth_wrapper() validates these keys before use

## Params:

- directory: str, path to documents folder
- pinecone_index_name: str, pinecone index 
- chunk_size: int, size of doc splits
- model_name: str, embedding model name  
- chain_type: str, Langchain QA model type

