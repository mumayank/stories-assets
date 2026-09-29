# stories-assets

Public static assets for the Stories Android app. The app fetches
`manifest.json` and downloads the listed packs with a resumable background
bootstrap; the manifest schema, base URL constant and consumer details live
in the app repository's `docs/lazy-assets.md`.

- `manifest.json` - one entry per asset, sorted smallest bytes first:
  `{"assets":[{"id","url","bytes","sha256"}]}`.
- `fonts-v1.zip` - the reader font pack: 21 families (83 faces) plus their
  OFL license texts under `licenses/`.

## Regenerating the font pack

Copy the font faces and license texts from the legacy repository's
`composeResources/font` and `composeResources/files/font-licenses` into a
staging directory (faces at the root, licenses under `licenses/`), zip them
into `fonts-v1.zip` at the repository root, then rewrite `manifest.json`
with the new byte count and sha256 of that zip. Keep `id` values stable: the
app keys its download and resume state by them.
