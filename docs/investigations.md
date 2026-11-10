# Endpoint forensic investigations

## Processes and TCP sockets — local VQL

The separate local investigation produced **219 process rows** and **17 TCP entries**. Seven socket entries were reported as listening and ten as established.

For process triage, relevant dimensions include PID, parent PID, executable, username and creation time. A process name or network connection is **not by itself** evidence of maliciousness; analyst review requires context and correlation.

## Local accounts and login history — server collections

- `Linux.Sys.Users`: **59** records.
- `Linux.Sys.LastUserLogin`: **41** records.
- `Linux.Syslog.SSHLogin`: **0** records; collection completed. A zero-row result does not establish the absence of all SSH use.

The separate local journal analysis classified **271** authentication-related events under its selected filters (168 other events, 51 session opens, 51 closes and 1 classified failure). These are historical observations, not an attribution to an attacker.

## Sample-file collection and integrity

`Generic.Collectors.File` acquired two authorized `.txt` samples and `System.VFS.ListDirectory` returned two `Listing` rows plus one `Stats` row. The independent local file results reported:

| Name | Size | Unix permissions | SHA-256 |
| --- | ---: | --- | --- |
| `inventory.txt` | 65 B | `-rw-rw-r--` | `8fabbf94bbf8d15c5a32a191be7a6323388b8e217f90c6b884685fefc031af18` |
| `notes.txt` | 77 B | `-rw-rw-r--` | `2ce9f19e27f66ab0d29b64eceebddee0ade3e52aff81516e7acabcbc22a187bb` |

These are **known synthetic test files**. Full contents, local absolute paths and raw endpoint records are omitted from Git.

`-rw-rw-r--` means a regular file whose owner/group have read/write access while others have read-only access. The VFS result shows recorded metadata; it is not a bit-for-bit forensic disk image.

See [`examples/sample-file-metadata.json`](../examples/sample-file-metadata.json) for a safe structured representation.
