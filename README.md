# Home Assistant Add-on: RIPE Atlas Probe

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](LICENSE)

Run a [RIPE Atlas](https://atlas.ripe.net/) software probe directly inside Home Assistant, contributing Internet measurements to the global RIPE Atlas network.

## Add this repository to Home Assistant

1. Go to **Settings → Add-ons → Add-on Store**.
2. Click ⋮ → **Repositories**.
3. Paste `https://github.com/JosephBlock/HA-Atlas` and click **Add**.
4. Search for **RIPE Atlas Probe** and install it.

## Quick Start

1. Add this repository to Home Assistant (see below) and install the **RIPE Atlas Probe** add-on.
2. Start the add-on — it will generate an SSH key pair on first boot.
3. Open the add-on **Log** tab and copy the public key printed between the `====` lines.
4. Paste it at <https://atlas.ripe.net/apply/swprobe/> to register your probe.

## Repository Structure

```
├── repository.json          # HA add-on repository descriptor
├── ripe-atlas/
│   ├── config.yaml          # Add-on manifest
│   ├── Dockerfile           # Extends jamesits/ripe-atlas
│   ├── run.sh               # Startup shim — injects reg_key into the container
│   └── DOCS.md              # User-facing documentation
└── README.md
```

## Requirements

| Requirement | Details |
|-------------|---------|
| Home Assistant | Supervisor / OS (not Home Assistant Container) |
| Architecture | `amd64`, `aarch64`, `armhf`, `armv7` |
| Network | Outbound TCP 443 must be open |
| RIPE Atlas account | Free — <https://atlas.ripe.net/> |

## Credits

- Upstream probe Docker image: [jamesits/docker-ripe-atlas](https://github.com/jamesits/docker-ripe-atlas)
- RIPE Atlas software probe: [RIPE NCC](https://atlas.ripe.net/)
