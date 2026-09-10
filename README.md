# Kintone's OpenAPI Specification

This repository contains the OpenAPI specification for Kintone's REST API.

> [!NOTE]
> Regenerated every day, and committed only when the content changed. Do not edit these files by
> hand — the next run replaces them.

- [Concept](#concept)
- [Usage](#usage)
- [Versions](#versions)
- [Releases](#releases)
- [Limitations](#limitations)
- [Feedback](#feedback)
- [License](#license)

## Concept

OpenAPI is a specification format for describing REST API interfaces. What it produces is both human-
and machine-readable, and it is widely supported by API tooling, so a file like this one lets you
inspect requests in Postman, generate a client library, or have an AI agent call the API correctly.

The text attached to each operation, parameter and field is the wording from the official
[API reference](https://kintone.dev/en/docs/kintone/rest-api/), so a tool reading these files shows
what a developer would read.

Every endpoint Kintone's own metadata API reports is described, including the guest-space form
(`/k/guest/{guestSpaceId}/v1/...`) of each one, together with the authentication each endpoint accepts.
Reading and writing are kept apart where they differ: `RecordObject` describes what comes back,
`RecordWritableObject` what you send.

## Usage

| File | Description |
| --- | --- |
| `openapi.yaml` | The whole specification bundled into a single file. |
| `openapi.json` | The same bundle, serialized as JSON. |
| `paths/` , `components/` | The same specification split up, one file per endpoint and per schema, linked with the `$ref` keyword. Read a single type here, or use it to see what changed between commits. |

YAML and JSON carry the same document, so take whichever your tool prefers. Reach for a bundled file
rather than the split-up version unless you need the parts: Postman and Microsoft Copilot Studio, among
others, cannot resolve references between files.

These files are OpenAPI 3.0.3. The server URL carries a `subdomain` variable whose
default, `example`, is a placeholder: replace it with your own subdomain, or a tool that imports
the file as it stands will call `https://example.cybozu.com`.

## Versions

`info.version` is **the date the content last changed** (JST, `YYYY.M.D`), not the date of the run
that produced the file. A run that finds nothing changed commits nothing, so the version you see is
the day this specification last moved. The commit history is the record of what changed and when.

## Releases

The `main` branch always carries the current specification. New tags are created in sequence
(`v1`, `v2`, …).

Each [release](../../releases) includes the bundled specification files as they existed at the time of
the release. The date the files were generated is recorded in their `info.version` field.

If you need to use a fixed version of the specification, pin your integration to a tag. For example, use
a raw URL with the tag name in place of the branch name. Because tags are never moved to newer commits,
a URL pinned to `v1` will continue to serve the same content in the future.

A new tag is created only when the specification has changed since the previous release, so each tag
represents a distinct version of the specification.

## Limitations

- The API interface is based on the Kintone REST API in the **Current Channel**, with all **Update
  Options** checkboxes left unchecked. Endpoints that need a preview feature switched on are not
  described.
- English only.
- The OAuth2 scope on each operation is a best-effort estimate: Kintone publishes no
  machine-readable mapping from endpoint to scope.
- Session authentication is out of scope. It is meant for customizations running inside a browser,
  not for the clients this specification is aimed at.
- These files come from an in-house generator that is not published, and they are not written against
  any particular client generator. Every build has to pass Redocly's linter and a set of further
  checks of our own, and is verified to load with `openapi-typescript`; other toolchains,
  `openapi-generator` among them, are not tested.

## Feedback

If something here is wrong — an endpoint that does not match the API, a field described the wrong way
round, a description that contradicts the reference — write to
[developer@cybozu.com](mailto:developer@cybozu.com). Include the operation or schema name; a link to
the file at a commit is ideal.

Issues are not enabled on this repository. Nothing here is edited by hand, so a fix has to go into the
generator that produces these files, which is why reports come to us by mail rather than as pull
requests. For questions about using the API itself, start from the
[API reference](https://kintone.dev/en/docs/kintone/rest-api/).

## License

MIT No Attribution (`MIT-0`). See [`LICENSE`](LICENSE). It is the MIT license without the
attribution clause, so you can copy, modify, and redistribute this specification — in your own
repository, in a generated client, or in fragments — without carrying the copyright notice along.
