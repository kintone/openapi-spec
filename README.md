# kintone OpenAPI spec

OpenAPI description for the kintone REST API.

> [!NOTE]
> Generated once a day. Do not edit these files by hand — the next run replaces them.

- [Concept](#concept)
- [Usage](#usage)
- [Versions](#versions)
- [Releases](#releases)
- [Limitations](#limitations)
- [Coming from kintone/rest-api-spec](#coming-from-kintonerest-api-spec)
- [License](#license)

## Concept

OpenAPI is a specification for describing REST API interfaces. It is both human- and machine-readable,
and it is widely supported by API tooling, so a description like this one lets you inspect requests in
Postman, generate a client library, or have an AI agent call the API correctly.

This repository holds that description for the kintone REST API. The text attached to each operation,
parameter and field is the wording from the official
[API reference](https://kintone.dev/en/docs/kintone/rest-api/), so a tool reading these files sees
what a developer would read.

Every endpoint kintone's own metadata API reports is described, including the guest-space form
(`/k/guest/{guestSpaceId}/v1/...`) of each one, together with the authentication each endpoint accepts.
Reading and writing are kept apart where they differ: `RecordObject` describes what comes back,
`RecordWritableObject` what you send.

## Usage

| File | Description |
| --- | --- |
| **`openapi.yaml`** | A bundled, single-file version of the API description, for tools that do not support the `$ref` keyword. **Start here.** |
| `openapi.json` | The same bundled description, serialized as JSON. |
| `paths/` , `components/` | A multi-file version of the same description, one file per endpoint and per schema, linked with the `$ref` keyword. Read a single type here, or use it to see what changed between commits. |

Point your tool at `openapi.yaml` unless you have a reason not to. Postman and Microsoft Copilot
Studio, among others, cannot resolve references between files and need the bundled version.

## Versions

`info.version` is **the date the content last changed** (JST, `YYYY.M.D`), not the date of the run
that produced the file. A run that finds nothing changed commits nothing, so the version you see is
the day this description last moved. The commit history is the record of what changed and when.

## Releases

The default branch always carries the current description. Once a month a tag is added, named after
the year and month in JST (`YYYY.MM`), and the [release](../../releases) for it attaches the bundled
files as they stood at that point.

Pin a tag when you need the description to stop moving under you: a tagged raw URL, with the tag in
place of the branch name, keeps serving the same bytes. A tag is added only when the description
changed since the previous one, so no two tags carry the same content.

## Limitations

- The API interface is based on the kintone REST API in the **Current Channel**, with all **Update
  Options** checkboxes left unchecked. Endpoints that need a preview feature switched on are not
  described.
- English only.
- The OAuth2 scope on each operation is a best-effort estimate: kintone publishes no
  machine-readable mapping from endpoint to scope.
- Session authentication is out of scope. It is meant for customizations running inside a browser,
  not for the clients this description is aimed at.

## Coming from `kintone/rest-api-spec`

- The bundled description is at the repository root (`openapi.yaml`). There is no `bundled/` directory, and no directory per publication date — the commit history is how you look at an older state.
- `paths/` and `components/schemas/` keep the same file names, so a file you used to open is where you expect it.
- Field-value schemas are shared instead of copied per operation: `RecordGetCalcSimpleValue`, `BulkRequestPostCalcSimpleValue` and the rest are now a single `CalcSimpleValue`. Update any `$ref` that pointed at a per-operation name.

## License

MIT No Attribution (`MIT-0`). See [`LICENSE`](LICENSE). It is the MIT license without the
attribution clause, so you can copy, modify, and redistribute this description — in your own
repository, in a generated client, or in fragments — without carrying the copyright notice along.
