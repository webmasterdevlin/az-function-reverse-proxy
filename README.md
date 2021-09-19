## Reverse Proxy for jsonplaceholder.typicode.com

### Requirements

- proxies.json with routes

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "resource": {
      "matchCondition": {
        "methods": ["GET", "POST"],
        "route": "{resource}"
      },
      "backendUri": "https://jsonplaceholder.typicode.com/{resource}",
      "responseOverrides": {
        "response.headers.Content-Type": "application/json",
        "response.headers.x-api-key": "%SECRET%"
      }
    }
  }
}
```

### With

- fake api key setup by editing local.settings.json

- edit local.settings.json

```json
{
  "IsEncrypted": false,
  "Values": {
    "AzureWebJobsStorage": "",
    "FUNCTIONS_WORKER_RUNTIME": "node",
    "SECRET": "my_secret"
  }
}
```
