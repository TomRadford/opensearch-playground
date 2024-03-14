Updating useful when you only want to change some
of the fields:

```bash
POST weather-data/_update/1
{
    "doc" : {
        "rainfall-rate": 0.5,
        "observation": "cloudy"
    }
}

```

doc block tells ES that we're updating part of the OG document.
we update rainfall-rate and add observation

result:

```json
...
  "_index": "weather-data",
  "_id": "1",
  "_version": 2,
  "result": "updated", <-- yay
 ...
```

and posting again will result in:

```json
"result": "noop"
```
