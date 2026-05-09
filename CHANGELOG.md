# Changelog

## v0.9.1 - 2026-05-09

- Added a local vendor database compiler based on the official IEEE MA-L, MA-M, and MA-S registries.
- Improved manufacturer detection by preferring the local IEEE dataset over raw `arp-scan` text.
- Added cautious heuristics for randomized private MAC addresses.
- Removed duplicate `arp-scan` entries from the final device list.
- Added `--version` support.
