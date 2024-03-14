#see https://www.youtube.com/watch?v=YtcOkJ33RGg&list=PLArPZXE1kgwyQhFINDVNxlnI8ASAwyKik&index=6

Text --> going into a field of type `text` is analysed

Keywords --> are not analysed but for exact matches, ordering or aggs.

IP --> seperate so we can query based on subnet

Geo --> all docs within a bounding box

Range --> eg integer/ip/date range hold two

```json
PUT mappings-demo
{
  "mappings": {
    "properties": {
      "my_number": {
        "type": "half_float"
      },
      "my_text": {
        "type": "text"
      },
      "my_keyword": {
        "type": "keyword"
      },
      "my_ip": {
        "type": "ip"
      },
      "my-geo": {
        "type": "geo_point"
      },
      "my_int_range": {
        "type": "integer_range"
      },
      "my_ip_range": {
        "type": "ip_range"
      },
      "my_date_range": {
        "type": "date_range"
      },
      "my_float_range": {
        "type": "float_range"
      }
    }
  }
}
```

Creating a doc with the ranges:

```json
POST mappings-demo/_doc
{
    "my_int_range": {
        "gte": 30,
        "lte": 39
    },
    "my_ip_range": "10.0.1.0/24",
    "my_geo": {
        "lat": 0,
        "lon": 0
    }
}
```
