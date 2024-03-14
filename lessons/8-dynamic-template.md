Allows you to match certain rules:

- like field name
- or mapping type

```json
// PUT dynamic
{
  "mappings": {
    "dynamic_templates": [
      {
        "long_as_short": {
          "match_mapping_type": "long",
          "mapping": {
            "type": "short"
          }
        }
      }
    ]
  }
}
```

it matches any new long types as short types...
if there's a new field if it picks up as long,
it should map as short.

We can also map based on field range.
