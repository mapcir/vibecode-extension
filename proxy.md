# 🌐 Proxy Configuration

Vibe Code supports both HTTP and SOCKS5 proxies, which is ideal for corporate environments or for bypassing geographical restrictions.

## Configuration Formats

You can configure the proxy in `.vibeconfig.json` using either a simple string or a detailed object.

### 1. URL String Format (Recommended)

**HTTP Proxy:**
```json
{
    "proxy": "http://127.0.0.1:8080"
}
```

**SOCKS5 with Authentication:**
```json
{
    "proxy": "socks5://username:password@127.0.0.1:1080"
}
```

### 2. Object Format

**SOCKS5 Proxy with Authentication:**
```json
{
    "proxy": {
        "enabled": true,
        "type": "socks5",
        "host": "127.0.0.1",
        "port": 1080,
        "auth": {
            "username": "your_username",
            "password": "your_password"
        }
    }
}
```

## SSH Tunnel Setup

To use an SSH tunnel as a SOCKS5 proxy:

1.  **Create the tunnel**:
    ```bash
    ssh -D 1080 -C -N user@your-server.com
    ```
2.  **Configure `.vibeconfig.json`**:
    ```json
    {
        "proxy": "socks5://127.0.0.1:1080"
    }
    ```

## Disabling Proxy

To disable the proxy, you can either:
1. Remove the `proxy` field from your configuration.
2. Set `enabled: false` in the object format:
```json
{
    "proxy": {
        "enabled": false
    }
}
```

---
[← RAG & Indexing](rag.md) | [Back to README](../README.md)
