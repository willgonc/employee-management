# API Contract: MVP RSS Subscriptions

## Base URL
`/api/subscriptions`

## Endpoints

### GET /api/subscriptions
Response: 200 OK
Body: JSON array of Subscription objects

### POST /api/subscriptions
Request: JSON body `{ "url": "https://example.com/feed" }`
Response: 201 Created
Body: Created Subscription object with `id` and `url`

### DELETE /api/subscriptions/{id}`
Request: Path parameter `id` (GUID)
Response: 204 No Content (if existed) or 404 Not Found

## Subscription object
```json
{
  "id": "00000000-0000-0000-0000-000000000000",
  "url": "https://example.com/feed"
}
```

## Notes
- All input is treated as untrusted; server will validate that `url` is a non-empty string. URL format validation is optional for MVP and may be deferred.
- No authentication is required for MVP.
