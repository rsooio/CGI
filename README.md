# CGI

Minimal Apache HTTPD + CGI sandbox via Docker Compose.

## Usage

```bash
docker compose up -d
```

## Developing CGI Scripts

Drop an executable script into `api/` and it's served at `/api/<name>`. The CGI protocol:

1. Read the request body from stdin
2. Write response headers to stdout
3. One blank line after headers
4. Write the response body

Example — `api/health`:

```bash
#!/bin/bash

read body

echo "Content-Type: text/plain"
echo
echo "OK"
```

Access it at <http://localhost:8080/api/health>.

## Files

| File           | Purpose                           |
|----------------|-----------------------------------|
| `compose.yaml` | Docker Compose setup (Apache 2.4) |
| `httpd.conf`   | Apache config, minimal CGI-only   |
| `api/`         | CGI scripts directory             |
