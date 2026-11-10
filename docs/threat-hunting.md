# Controlled hash hunting

## Purpose

Validate that a Velociraptor hunt can target the intended Linux endpoint and identify files matching known SHA-256 digests. **This was a functionality check with benign files, not malware hunting in a compromised host.**

## Procedure

1. Compute the two test-file SHA-256 digests independently.
2. Create a restricted hunt using built-in `Generic.Detection.HashHunter`.
3. Restrict targets by an explicit, temporary label covering only the laboratory client.
4. Verify the membership before starting the hunt.
5. Inspect the completed client flow and expected result rows.
6. Stop the hunt after verification.

## Observed outcome

| Field | Observed |
| --- | --- |
| Target count | 1 Linux client |
| Source files | 2 controlled sample files |
| Matches | 2 expected SHA-256 matches |
| Hunt | Stopped after checking results |
| Client flow | Finished |

A match means that a file hash matched an input digest. A hash match alone does not prove a file is malicious. The hunt's internal IDs and label have been intentionally removed from this public summary.

See the [official hunting documentation](https://docs.velociraptor.app/docs/hunting/).
