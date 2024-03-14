`Select * from TABLE`

```json
GET _search
{"query": {
  "match_all": {}
}}

```

res contains the took time in ms and hits with `_score` ranking (which refers to relevance).
Default score === 1.
