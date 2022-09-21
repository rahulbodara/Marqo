# Marqo

## Getting started

1. Marqo requires docker. To install docker go to https://docs.docker.com/get-docker/

2. Use docker to run Marqo (Mac users with M-series chips will need to [go here](#m-series-mac-users)):

```bash
docker rm -f marqo;docker run --name marqo -it --privileged -p 8882:8882 --add-host host.docker.internal:host-gateway marqoai/marqo:0.0.3
```

3. Install the Marqo client:

```bash
pip install marqo
```

4. Run python file 
```bash
    python start.py
```

5. test in postman with curl command(optional)
```bash
http://localhost:8882/indexes/my-first-index/documents/article_591
```



## Other basic operations

### Get document
Retrieve a document by ID.

```python
result = mq.index("my-first-index").get_document(document_id="article_591")
```

Note that by adding the document using ```add_documents``` again using the same ```_id``` will cause a document to be updated.

### Get index stats
Get information about an index.

```python
results = mq.index("my-first-index").get_stats()
```

### Lexical search
Perform a keyword search.

```python
result =  mq.index("my-first-index").search('marco polo', search_method=marqo.SearchMethods.LEXICAL)
```

### Search specific fields
Using the default tensor search method
```python
result = mq.index("my-first-index").search('adventure', searchable_attributes=['Title'])
```

### Delete documents
Delete documents.

```python
results = mq.index("my-first-index").delete_documents(ids=["article_591", "article_602"])
```

### Delete index
Delete an index.

```python
results = mq.index("my-first-index").delete()
```