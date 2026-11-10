# Investigation scope and methodology

## Scope

One personally controlled Kali VM (Linux AMD64) running server and client locally. No external endpoints were enrolled in the demonstrated investigation. Synthetic files were intentionally created for integrity and hunting checks.

## Evidence classes

| Evidence category | Collection method | Notes |
| --- | --- | --- |
| Six artifacts | Server-scheduled endpoint **flows** | State reported `FINISHED`; artifact row counts vary by source |
| Process/network/journal observations | Separate local read-only VQL execution | Do **not** represent these numbers as server flow output |
| Hash hunt | Server-controlled single-client hunt | Two expected benign-file matches |
| Notebook | Query against a previously stored VFS flow | Reading stored rows is not a new endpoint collection |
| Custom artifact definition | GUI catalog registration | Registration confirmed, complete independent flow not confirmed |

## Validation sequence

1. Check that the service is running and the test endpoint is connected.
2. Identify the artifact name and exact source name.
3. Confirm the flow's state (`FINISHED` or another state) and capture collection timestamps.
4. Retrieve relevant rows, noting zero-row results and source breakdowns.
5. Hash controlled files independently and compare expected digests.
6. Label the single endpoint before running a limited hunt and verify membership.
7. Examine the notebook using the correct `Listing` source.
8. Document uncertainty and avoid labeling benign test indicators as threats.

## Evidence handling

The archive used for validation contained raw system information, authentication-related records, local paths and identifiers. **None** of those raw JSONL outputs were copied into this public repository. Only an allowlisted count summary and two safe sample-file metadata records are exposed in `examples/`. The screenshots are derivatives cropped to exclude browser chrome and manually redacted where necessary.
