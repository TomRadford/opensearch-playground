Disable dynamic mappings for the index.

Reject documents not in our index:

```json
PUT weather-data-2
{
  "mappings": {
    "dynamic": "strict"
    ...
```

This prevents `field count explosion` where new documents with new
data create new fields on the mapping.

However... this will throw and not allow any doc with fields not in the mapping
to be index.

A nicer middle ground could be:

```json
{
"mappings": {
"dynamic": false
...
}
```

this allows us to add docs with new fields not in the index
while preventing them from being added to the index.
However, this will still be in the `_source`.
(but we can't use it for queries)

Large number of fields in an index with affect cluster perf. (can be changed in `index/_settings`)

If you need to change the data type for an existing field:

- Create a new index with your new mapping
- Bring documents over in a re-index operation
