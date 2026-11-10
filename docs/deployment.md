# Deployment walkthrough

This document explains the **observed installation sequence** for a single-endpoint local laboratory. It is not a turn-key unattended installer; generate unique certificates, secrets and credentials for any new deployment.

## 1. Prepare a guest

Run a Kali Linux AMD64 guest with enough memory and disk for Velociraptor's services and evidence store. The observed environment was approximately 5.8 GiB RAM and 30 GiB initially free.

## 2. Obtain and verify Velociraptor

Use the [official downloads](https://docs.velociraptor.app/downloads/) or [versioned release](https://github.com/Velocidex/velociraptor/releases/tag/v0.77.3), choose **Linux AMD64**, and verify the SHA-256 checksum from the correct release artifact. A compressed `.gz` and its extracted binary have **different** digests, so do not compare the archive hash to the extracted binary.

## 3. Generate isolated configurations

The local server and endpoint were configured using the supported Velociraptor CLI. Authentication/certificate material belongs outside version control. The server was constrained to loopback and an administrative GUI identity was created locally.

## 4. Install and activate services

The deployment generated Debian `.deb` server and client packages and installed them using the system package manager. The resulting Linux services were named:

- `velociraptor_server.service`
- `velociraptor_client.service`

For an existing lab, verification commands are:

```bash
systemctl is-active velociraptor_server.service velociraptor_client.service
ss -lnt | grep -E ':8000|:8001|:8003|:8889'
```

Both services were observed as `active` and the expected local listeners were present.

## 5. Validate GUI and enrollment

Open `https://127.0.0.1:8889` **within Kali**, use the local administrator credentials and inspect the client search screen. The test agent appeared as `kali` with green connected status and agent version **0.77.3**.

A self-signed laboratory TLS certificate may prompt the browser to request additional trust confirmation. Verify the certificate intentionally; do not disable TLS checks for a production deployment.

## 6. Verify evidence persistence

After an unexpected VM shutdown, check service state, connectivity, completed flows and notebook results before assuming data was lost or reinstalling. Keep backup copies of any sensitive raw evidence **outside the public repository**.

**Security:** Never copy your live `/etc/velociraptor/` configurations, API certificates, passwords, private keys or datastore to a public repository.
