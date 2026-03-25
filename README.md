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
    comment-mode: none
    cloud-url: <cloud-url>
```

## Inputs

| Name              | Required | Description                                                                     |
| ----------------- | -------- | ------------------------------------------------------------------------------- |
| `stage`           | Yes      | The name of the stage                                                           |
| `client-id`       | Yes      | The ID of the client                                                            |
| `api-key`         | Yes      | API key for authentication                                                      |
| `operations-file` | Yes      | The path to the JSON file with the operations                                   |
| `comment-mode`    | No       | Pull request feedback mode on failure: `comment`, `review`, or `none` (default) |
| `cloud-url`       | No       | The URL of the Nitro registry                                                   |

If you self-host Nitro or use a dedicated hosted instance, you can specify the `cloud-url` input to point to your instance.

## Pull Request comments

Use `comment-mode` to control pull request feedback behavior.

`comment-mode: comment` comments on the pull request - requires `issues: write` permissions

`comment-mode: review` creates a pull request review with a comment - requires `pull-requests: write` permissions

Example for `comment-mode: comment`:

```yaml
jobs:
  validate:
    permissions:
      contents: read
      issues: write
```

Example for `comment-mode: review`:

```yaml
jobs:
  validate:
    permissions:
      contents: read
      pull-requests: write
```

> Note: When you define job-level `permissions`, GitHub no longer applies the default permission set for that job. Make sure to explicitly include every permission the job needs (for example `contents: read`).
