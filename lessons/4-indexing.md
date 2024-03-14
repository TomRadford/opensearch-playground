creating a new index

```bash
PUT weather-data2
```

RES:

```
{
  "acknowledged": true,
  "shards_acknowledged": true,
  "index": "weather-data2"
}
```

this will create an index with the defaults

Create an index with settings/mappings:

```bash
PUT weather-data2
{
    "settings": {
        "number_of_shards": 1, <-- number of primary shard to use for the index
        "number_of_replicas": 0 <-- number of replica shards per primary shard
    }
}
```

Mapping === structure of the index' documents and how it stores the data - this affects what you can query

Every index has a mapping!

View mapping with:

```bash
GET weather-data/_mapping

returns:
{
  "weather-data": {
    "mappings": {
      "properties": {
        "observation": {
          "type": "text",
          "fields": {
            "keyword": {
              "type": "keyword",
              "ignore_above": 256
            }
          }
        },
        "pressure": {
          "type": "long"
        },
        "rainfall-rate": {
          "type": "float"
        },
        "station-id": {
          "type": "long"
        },
        "temperature": {
          "type": "float"
        },
        "timestamp": {
          "type": "date"
        },
        "wind-direction": {
          "type": "text",
          "fields": {
            "keyword": {
              "type": "keyword",
              "ignore_above": 256
            }
          }
        },
        "wind-speed": {
          "type": "float"
        }
      }
    }
  }
}
```

--> returns the mapping (which is like a schema with field types)
derived from the first document we index

Mappings are critical to ES!

Creating a mapping:

```json
PUT weather-data-2
{
  "mappings": {
    "properties": {
      "observation": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword",
            "ignore_above": 256
          }
        }
      },
      "pressure": {
        "type": "long"
      },
      "rainfall-rate": {
        "type": "float"
      },
      "station-id": {
        "type": "long"
      },
      "temperature": {
        "type": "float"
      },
      "timestamp": {
        "type": "date"
      },
      "wind-direction": {
        "type": "text",
        "fields": {
          "keyword": {
            "type": "keyword",
            "ignore_above": 256
          }
        }
      },
      "wind-speed": {
        "type": "float"
      }
    }
  }
}
```
