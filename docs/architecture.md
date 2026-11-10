# Architecture and trust boundaries

The laboratory ran both Velociraptor server and Linux client on the **same Kali Linux Rolling 2026.3 VM** under UTM. The host computer ran macOS; the experiment did not require a routable, remote endpoint.

| Component | Local role |
| --- | --- |
| Server | Controls client tasks, stores flow outputs, exposes GUI and optional automation APIs |
| Agent / client | Collects requested endpoint telemetry and responds to the server |
| Frontend (`127.0.0.1:8000`) | Encrypted endpoint-to-server communication |
| Admin GUI (`https://127.0.0.1:8889`) | Operator access to clients, artifacts, flows, hunts and notebooks |
| gRPC API (`127.0.0.1:8001`) | Authenticated programmatic queries and orchestration |
| Monitoring (`127.0.0.1:8003`) | Local server monitoring listener in the observed configuration |
| Datastore | Local evidence storage (service-managed; not committed to Git) |

`127.0.0.1` is loopback. A local listener is *not* automatically reachable from the host or other VMs. A separately configured enterprise deployment would require deliberate network configuration, access controls, certificate management, storage design, and retention policies.

## Data flow

1. The analyst selects a built-in or custom artifact.
2. The server schedules an endpoint collection flow.
3. The agent executes the approved queries and returns data over TLS.
4. The server persists results and records collection metadata.
5. The analyst opens results in the GUI or queries them from notebooks, using the exact artifact source.

A **hunt** schedules artifact collections across matching endpoints. This experiment restricted its hunt to one labeled Linux client.
