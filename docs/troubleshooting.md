# Troubleshooting notes

The following issues occurred during setup or analysis and were resolved or bounded during the lab. They are included because failure diagnosis is part of DFIR operations.

| Symptom | Interpretation | Practical check or correction |
| --- | --- | --- |
| Download checksum comparison appears inconsistent | The compressed archive and extracted executable have different digests | Compare each artifact to its corresponding published checksum |
| GUI does not load immediately | Server service, listener, certificate or browser issue | Verify service state and local `:8889` listener before changing networking |
| Agent missing from client search | Enrollment or service connectivity not verified | Inspect client service state and GUI last-seen information |
| Cannot edit service-managed datastore as root | File ownership and service-account restrictions | Run service-supported administrative operations as the appropriate service user |
| Local VQL result differs from server flow counts | Different execution and storage contexts | Label local CLI queries separately from server collections |
| Notebook displays `Table contains no data` | Artifact sub-source was not selected | Inspect available sources; use `source="Listing"` for VFS listing rows |
| VM unexpectedly shuts down | Runtime loss does not imply deleted disk-backed results | Boot the existing VM, check services, notebook and saved flows before reinstalling |
| Hunt could target unintended clients | Search condition too broad | Test target label and client membership before starting; halt after verification |

Operational discipline: diagnose service state, logs, connectivity, artifact source and collection status in that order, instead of modifying multiple components at once.
