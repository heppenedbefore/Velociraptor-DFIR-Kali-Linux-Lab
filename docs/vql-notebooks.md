# VQL and investigation notebooks

## Core concepts

**VQL (Velociraptor Query Language)** allows investigators to query endpoints and inspect saved forensic information. A **notebook** is a persistent workspace for queries, results and notes. Reading a completed collection from a notebook **does not dispatch a new collection**.

## Verified notebook workflow

A global notebook named **Kali DFIR Investigation** was used to test VQL execution and then retrieve a previously collected directory listing. Its smoke test yielded `Test_OK = 1`.

An initial retrieval returned `0` rows because it omitted the relevant artifact sub-source. The collection had:

- `System.VFS.ListDirectory/Listing`: **2** file-metadata records
- `System.VFS.ListDirectory/Stats`: **1** collection-statistics record

Specifying `source="Listing"` returned the two file records and `RowsScanned = 2`.

## Reusable query template

See [`queries/read_saved_vfs_listing.vql`](../queries/read_saved_vfs_listing.vql). Replace *both* placeholder IDs with your own existing flow identifiers in the authorized environment.

## Reading the output

- `Name`: filename.
- `Size`: bytes.
- `Mode`: Linux file type and access permissions.
- `mtime`: recorded file-content modification timestamp.

You may also use the **Notebook** tab attached to a completed collection to access a contextual notebook that knows its flow's collection scope.

Official reference: [`flow_results()`](https://docs.velociraptor.app/vql_reference/server/flow_results/).
