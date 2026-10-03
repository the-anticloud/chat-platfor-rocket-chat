# Technical Architecture — ROCKET_CHAT

**Upstream:** [https://github.com/RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat)
**License:** MIT
**Category:** CHAT_PLATFORMS
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

Self-hosted Slack alternative

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local moderation and response suggestions — no API calls
2. AIOSS append-only message audit chain (GDPR Article 30 compliant)
3. AES-256 end-to-end encryption for all messages and media
4. Single-binary self-hosted chat server — no cloud provider
5. Zero-cloud: all AI features, moderation, and search run locally
6. GPU/CPU equalizer: moderation inference scales to available hardware
7. Zero-telemetry: removes all usage tracking and profiling
8. Open Matrix/XMPP federation replacing proprietary protocols

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_rocket_chat.spec` or `go build -o rocket_chat`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |