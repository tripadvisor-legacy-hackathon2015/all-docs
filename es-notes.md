## elasticsearch notes

### Guides

You'll need to refer to ElasticSearch documentation to learn.

**Reference** 
https://www.elastic.co/guide/en/elasticsearch/reference/1.7/index.html

* Query DSL https://www.elastic.co/guide/en/elasticsearch/reference/1.7/query-dsl.html

**ES The Definitive guide** https://www.elastic.co/guide/en/elasticsearch/guide/current/index.html

### What will we use ES for?

ElasticSearch is a clustered solution for storing and retrieving documents.

You define: 
* indices
* document types (mappings) within indices
* documents `{ 'field': 'value' }`

### Some Demos

Create an index <br/>
`PUT fooindex`

Create a mapping within it
```
PUT fooindex/_mapping/mydoc
{
  "properties" : {
    "name": {"type":"string"}
  }
}


GET fooindex/_mapping/
```

Do some indexing and querying
```
POST fooindex/mydoc
{
  "name": "deCODE 2015",
  "description": "foobar"
}


GET fooindex/mydoc/_search
{
  "query": {
    "terms": {
    "name": ["lobster", "2015"]
    }
  }
}


```
