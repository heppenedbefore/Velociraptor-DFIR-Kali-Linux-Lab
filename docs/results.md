# Verified results and limitations

This table is derived from saved collection status objects, local read-only result counts, and actual GUI screenshots. The repo contains **derived summaries**, not sensitive raw evidence.

| Category | Result | Provenance |
| --- | --- | --- |
| Server and Linux agent | Both active; client online | Service-state inspection + GUI |
| Server-scheduled endpoint flows | 6 completed | Collection status objects |
| Client information | 22 rows across multiple sources | Server flow |
| Users | 59 | Server flow |
| Login history | 41 | Server flow |
| SSH login artifact | 0 rows, completed | Server flow |
| File acquisition | 2 files | Server flow |
| Directory listing | 2 rows + 1 stats row | Server flow |
| Process rows | 219 | **Local** VQL execution |
| TCP rows | 17 | **Local** VQL execution |
| Classified journal events | 271 | **Local** VQL execution |
| Targeted hash hunt | 2 known matches on 1 client | Completed hunt flow |
| Notebook output | 2 saved rows | GUI notebook |
| Custom artifact | Registered | GUI catalog only |

## What the evidence does *not* support

- A live real-world security incident, compromise or malware infection.
- A validated multi-client enterprise deployment.
- Proof that every source of the custom artifact was executed as an independently completed flow.
- Proof that zero SSH results means zero SSH activity globally.
- A full disk-image acquisition or complete historical reconstruction.

## Reproducibility note

The example file sizes are **65** and **77** bytes, confirmed in the collected VFS JSONL and GUI screenshots. Other derivative report drafts have shown different sizes; the figures here are based on the directly saved source records and the GUI screenshot, not on that discrepancy.
