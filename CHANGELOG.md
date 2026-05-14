# Changelog

## v1.0.0 - 2026-05-14

- **Signal handling**: SIGINT/SIGTERM now exits cleanly with a message instead of leaving zombie processes.
- **Parallel DNS resolution**: all reverse lookups now run concurrently via `ThreadPoolExecutor`, significantly reducing scan time on larger networks.
- **Gateway detection**: actual gateway IP is read from `ip route show default` and highlighted in output; no longer assumes `.1`.
- **`--subnet CIDR`**: scan a specific subnet instead of auto-detecting with `--localnet`.
- **`--no-bonjour`**: skip avahi-browse for faster scans.
- **`--json`**: machine-readable JSON output including `is_gateway`, `is_self`, and `services` fields.
- **`--csv`**: CSV output for use in scripts and spreadsheets.
- **`--timeout S`**: configurable arp-scan timeout (default: 15s).
- **`--api`**: query macvendors.com API for unknown MACs, with persistent local cache at `~/.local/share/ipscanner/api_cache.json`.
- Bumped version to 1.0.0.

## v0.9.1 - 2026-05-09

- Added a local vendor database compiler based on the official IEEE MA-L, MA-M, and MA-S registries.
- Improved manufacturer detection by preferring the local IEEE dataset over raw `arp-scan` text.
- Added cautious heuristics for randomized private MAC addresses.
- Removed duplicate `arp-scan` entries from the final device list.
- Added `--version` support.
