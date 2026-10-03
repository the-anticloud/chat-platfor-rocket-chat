# Build and Test

**Project:** `ROCKET_CHAT`
**Upstream:** https://github.com/RocketChat/Rocket.Chat
**License:** MIT

## Quick Start

```bash
git clone https://github.com/RocketChat/Rocket.Chat
cd Rocket.Chat
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local moderation and response suggestions — no API calls
2. AIOSS append-only message audit chain (GDPR Article 30 compliant)
3. AES-256 end-to-end encryption for all messages and media
4. Single-binary self-hosted chat server — no cloud provider
5. Zero-cloud: all AI features, moderation, and search run locally
6. GPU/CPU equalizer: moderation inference scales to available hardware
7. Zero-telemetry: removes all usage tracking and profiling
8. Open Matrix/XMPP federation replacing proprietary protocols

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
