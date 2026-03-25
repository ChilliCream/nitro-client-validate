# Nitro Client Validate

A GitHub Action that validates client operations against the Nitro registry.

## Usage

```yaml
- uses: ChilliCream/nitro-client-validate@v16
  with:
    stage: <stage>
    client-id: <client-id>
    api-key: <api-key>
    operations-file: ./path/to/operations.json
    # Optional
    cloud-url: <cloud-url>
```

## Inputs

| Name              | Required | Description                                   |
| ----------------- | -------- | --------------------------------------------- |
| `stage`           | Yes      | The name of the stage                         |
| `client-id`       | Yes      | The ID of the client                          |
| `api-key`         | Yes      | API key for authentication                    |
| `operations-file` | Yes      | The path to the JSON file with the operations |
| `cloud-url`       | No       | The URL of the Nitro registry                 |

If you self-host Nitro or use a dedicated hosted instance, you can specify the `cloud-url` input to point to your instance.
