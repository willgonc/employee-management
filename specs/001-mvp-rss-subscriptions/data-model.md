# data-model.md

## Entities

- **Subscription**
  - `id` (GUID) — internal identifier
  - `url` (string) — feed subscription URL

## Notes

- For MVP, subscriptions are stored in memory only.
- The `url` field is the required core attribute; additional metadata such as title or last fetched date is out of scope for this iteration.
