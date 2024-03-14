Get

```bash
GET weather-data/_doc/1

RES:
{
  "_index": "weather-data",
  "_id": "1",
  "_version": 4,
  "_seq_no": 6,
  "_primary_term": 1,
  "found": true,
  "_source": { <-- the document itself if found in here
    "timestamp": "2021-12-01T14:05:00Z",
    "station-id": 142,
    "temperature": 4.7,
    "wind-speed": 0.2,
    "wind-direction": "NNW",
    "pressure": 345,
    "rainfall-rate": 10
  }
}
```

Note: When you index a document, Lucene update a bunch of internal data structures
with details from your doc to make queries them fast/efficient.
Even though Lucene doesnt need the doc, its kept in the index in `_source`.

To get just the source:

```bash
GET weather-data/_source/1
```

Check if exists:

```bash
HEAD weather-data/_source/1
```

another way to get a doc is to run a query and read the results (the magic!)

```bash
GET weather-data/_search
{ "query": {
    "match_all": {}
}
```

which returns:

```json
{
  "took": 25,
  "timed_out": false,
  "_shards": {
    "total": 1,
    "successful": 1,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": {
      "value": 4,
      "relation": "eq"
    },
    "max_score": 1,
    "hits": [ .... <-- each of the 4 matched documents as hits (with all their es data and _source)
```

NOTE: es will only return `10` hits by default,
you can return more with:

```json
{
  "size": 100
  // rest of query
}
```
