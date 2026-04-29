# Production Deploy

## Services

Run the HTTP gateway and WebSocket gateway behind a reverse proxy. The WebSocket gateway handles text commands, binary audio buffering, ASR routing, and optional TTS audio frames:

```bash
PYTHONPATH=backend python3 -m ava_devicekit.cli run-http --host 0.0.0.0 --port 8788 --config runtime.local.json
PYTHONPATH=backend python3 -m ava_devicekit.cli run-firmware-ws --host 0.0.0.0 --port 8787 --config runtime.local.json
```

Use long proxy read timeouts for hardware sessions and keep WebSocket ping enabled through `websocket_ping_interval` and `websocket_ping_timeout`.

## Public URL Namespace

Do not expose the operator and customer pages directly at the domain root on shared servers. Keep public HTTP routes under a product namespace and let the backend strip that prefix internally. The default public prefix is `/ava-devicekit`.

| Public route | Internal route | Purpose |
|---|---|---|
| `/ava-devicekit/admin` | `/admin` | Operator dashboard |
| `/ava-devicekit/customer` | `/customer` | C-end activation portal |
| `/ava-devicekit/health` | `/health` | Gateway health check |
| `/ava-devicekit/manifest` | `/manifest` | Active app manifest |
| `/ava-devicekit/device/*` | `/device/*` | Device HTTP fallback/config/usage APIs |
| `/ava/ota/` | `/ava/ota/` | Firmware OTA entrypoint |
| `/ava/v1/` | WebSocket gateway | Firmware WebSocket |

Set `public_base_url` to the public namespace, for example `https://jupdev.tech/ava-devicekit`, so activation cards link to `/ava-devicekit/customer`. If a different prefix is required, set `AVA_DEVICEKIT_PUBLIC_PREFIXES=/your-prefix`.

Minimal nginx example:

```nginx
location /ava-devicekit/ {
    proxy_pass http://127.0.0.1:8788;
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-Prefix /ava-devicekit;
}

location /ava/v1/ {
    proxy_pass http://127.0.0.1:8787;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_set_header Host $host;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_read_timeout 86400s;
}
```

Local development may still use `/admin` and `/customer` directly on `127.0.0.1:8788`; the namespace rule is for public/shared domains.

## Runtime Safety

| Area | Rule |
|---|---|
| Secrets | Store only environment variable names in config files |
| Wallet signing | Use server-managed proxy/custodial wallet credentials on the backend; never store trade credentials on ESP32 |
| AI actions | Use deterministic routing for known actions and require physical confirmation for high-risk actions |
| OTA | Serve firmware only from the configured `firmware_bin_dir` |
| Admin APIs | Expose sanitized runtime state only; never return secret values |


## Auth

Set these environment variables to enable bearer-token protection. If they are unset, local development stays open.

| Env Var | Protects |
|---|---|
| `AVA_DEVICEKIT_ADMIN_TOKEN` | `/admin/*` endpoints |
| `AVA_DEVICEKIT_DEVICE_TOKEN` | `/device/*` endpoints |

Requests use `Authorization: Bearer <token>`. Device requests may also send `X-Ava-Device-Id` to bind state to a specific session.

## Multi-Device Runtime

The HTTP and generic WebSocket gateways use `RuntimeManager` to keep independent sessions by device id. Admin endpoints include:

| Path | Purpose |
|---|---|
| `/admin/devices` | List active device sessions |
| `/admin/devices/{device_id}/state` | Inspect one device session |
| `/admin/devices/{device_id}/outbox` | Inspect one device outbox |
| `/admin/events` | View recent runtime events |
