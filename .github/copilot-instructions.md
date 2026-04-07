# Home Assistant Add-on: RIPE Atlas Probe

## Project Overview
This is a Home Assistant Supervisor **add-on repository** that wraps the `jamesits/ripe-atlas` Docker image, allowing users to run a RIPE Atlas software probe directly from their Home Assistant instance.

## Project Structure
```
├── repository.json          # HA add-on repository descriptor
├── ripe-atlas/
│   ├── config.yaml          # Add-on manifest (name, version, options, arch, etc.)
│   ├── Dockerfile           # Extends jamesits/ripe-atlas; injects HA options
│   ├── run.sh               # Startup script — reads /data/options.json, sets RIPE_ATLAS_REG_KEY
│   └── DOCS.md              # User-facing add-on documentation
└── README.md                # Repository README
```

## Key Conventions
- **HA options** are injected at `/data/options.json` by the Supervisor at runtime.
- `run.sh` reads `reg_key` from that file and exports it as `RIPE_ATLAS_REG_KEY`.
- The add-on requires `host_network: true` and `privileged: true` for probe network access.
- `config.yaml` is the single source of truth for add-on metadata, options schema, and capabilities.

## Development Notes
- All add-on files live under `ripe-atlas/` (slug must match the directory name).
- To add a new user-facing option: add it to `options` (default) and `schema` (type) in `config.yaml`, then read it in `run.sh`.
- Supported architectures: `amd64`, `aarch64`, `armhf`, `armv7`.
