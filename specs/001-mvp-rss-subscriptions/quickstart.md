# Quickstart: MVP RSS Subscriptions

## Prerequisites
- .NET 8 SDK installed
- Browser to view the Blazor WebAssembly UI

## Run locally (backend + frontend)

```bash
# From repo root
# Start backend API (example path)
dotnet run --project backend/RSSFeedReader.Api/RSSFeedReader.Api.csproj

# Start frontend
dotnet run --project frontend/RSSFeedReader.UI/RSSFeedReader.UI.csproj
```

Open the frontend URL shown in the console and verify you can add a subscription URL and see it in the list.

## Manual verification
- Add a feed URL and confirm it appears in the list immediately.
- Try adding an empty string — observe the client-side rejection.
- Restart the app and verify subscriptions are cleared (in-memory storage).
