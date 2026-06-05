# LLM Inference Server

The platform provides a shared LLM inference endpoint that developers can use for AI-enhanced applications and coding assistance. The endpoint is compatible with the OpenAI API format, so any client library or tool that supports OpenAI can use it.

## Environment variables in DevSpaces

When working in OpenShift DevSpaces, the following environment variables are pre-configured in your workspace:

| Variable | Description |
|---|---|
| `LLM_BASE_URL` | Base URL of the inference endpoint (OpenAI-compatible `/v1` path) |
| `LLM_API_KEY` | API key for authenticating requests |

These are injected automatically — no setup required. You can use them directly in your application code or terminal:

```bash
curl -s -H "Authorization: Bearer $LLM_API_KEY" "$LLM_BASE_URL/models" | jq .
```

## Using in application code

The endpoint is OpenAI-compatible, so standard client libraries work out of the box:

```java
// Quarkus / LangChain4j
quarkus.langchain4j.openai.base-url=${LLM_BASE_URL}
quarkus.langchain4j.openai.api-key=${LLM_API_KEY}
```

```python
from openai import OpenAI

client = OpenAI(base_url=os.environ["LLM_BASE_URL"], api_key=os.environ["LLM_API_KEY"])
```

## Available models

The endpoint provides access to models hosted on the Red Hat Demo Platform's LiteMaaS instance. To list available models:

```bash
curl -s -H "Authorization: Bearer $LLM_API_KEY" "$LLM_BASE_URL/models" | jq '.data[].id'
```

## Vault credentials

For services that need to access the LLM endpoint outside of DevSpaces (e.g. from pipelines or backend services), the credentials are stored in HashiCorp Vault:

- **Path:** `kv/secrets/litellm/credentials`
- **Keys:**
    - `api_key` — API key for the inference endpoint
    - `base_url` — Base URL of the inference endpoint

These can be consumed via ExternalSecrets to inject credentials into any namespace on the cluster.
