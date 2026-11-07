# ReferenceCatalog

The central catalog of public reference libraries available to ANQL. It lists
libraries and links to their detailed catalogs; it does not contain the
resources themselves or their files.

## Files

- [`catalog.json`](./catalog.json) is the published catalog.
- [`catalog.schema.json`](./catalog.schema.json) defines and validates its structure.

The central catalog is intended to stay small and can be cached by clients.
Each published library provides its own resource catalog. Resources are
downloaded separately, only when explicitly selected by the user.

## Adding a library

Add an entry to `repositories` in `catalog.json` with these fields:

| Field | Description |
| --- | --- |
| `id` | A stable, unique identifier using lowercase letters, digits, or hyphens. Do not change it when the display name changes. |
| `name` | The library's display name. |
| `description` | A short description for users. |
| `catalogUrl` | The HTTPS URL of the library's detailed catalog. |

Publish the library catalog at a stable, public URL before proposing its entry
here. Verify that the URL uses HTTPS and that the detailed catalog matches the
declared identifier and name.

The central catalog currently lists only `ScienceReference`. Its detailed
catalog URL is reserved at
`https://raw.githubusercontent.com/anqlproject/ScienceReference/main/catalog.json`.
That file has not yet been published in the ScienceReference repository, so
the URL will not be available until the repository adds it.

## Versioning and compatibility

- `schemaVersion` identifies the document structure version. Incompatible
  structural changes require a new schema version.
- `catalogVersion` follows the `MAJOR.MINOR.PATCH` format and versions the
  catalog content independently of its schema.
- Catalog URLs must be served over HTTPS. Versioned, immutable URLs are
  recommended to preserve reproducibility.

Validate every catalog change against
[`catalog.schema.json`](./catalog.schema.json) before publication.
