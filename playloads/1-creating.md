Create new `Document` (which is one result in an index), any id

Here we create a new index called `weather-data` with it's first document

```bash
POST weather-data/_doc
{
"timestamp": "2021-11-01T14:05:00Z",
"station-id": 142,
"temperature": 14.7,
"wind-speed": 5.2,
"wind-direction": "SSE",
"pressure": 1023,
"rainfall-rate": 0.0
}
```

Create Specific id, can oly post once

```bash
POST weather-data/_create/1
{
"timestamp": "2021-11-01T14:05:00Z",
"station-id": 142,
"temperature": 14.7,
"wind-speed": 5.2,
"wind-direction": "SSE",
"pressure": 1023,
"rainfall-rate": 0.0
}
```

will create or update (result: updated, version no. increment),
NOTE: unlike `_update` this will replace the entire `_source` payload

```bash
PUT weather-data/_doc/1
{
"timestamp": "2021-12-01T14:05:00Z",
"station-id": 142,
"temperature": 4.7,
"wind-speed": 0.2,
"wind-direction": "NNW",
"pressure": 345,
"rainfall-rate": 10
}
```

another way of doing create

```bash
PUT weather-data/_doc/1?op_type=create
{
"timestamp": "2021-12-01T14:05:00Z",
"station-id": 142,
"temperature": 4.7,
"wind-speed": 0.2,
"wind-direction": "SE",
"pressure": 35,
"rainfall-rate": 10
}
```
