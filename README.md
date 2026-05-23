# ejamdata

Large datasets used by the [EJAM package](https://Public-Environmental-Data-Partners.github.io/EJAM/index.html).

## Authoritative data files

For installed EJAM packages, the authoritative data files are the `.arrow` files attached as **GitHub release assets** in this repository. EJAM downloads those release assets with `piggyback::pb_download()` using a release tag such as `v2.32.8.001` or `v2.5.0`.

The files committed in repository folders such as `data/` are not what EJAM installations normally download. Treat those committed files as maintainer convenience or historical working copies unless a specific maintenance task says otherwise. When there is any difference between files in the repository tree and files attached to a GitHub release, the release assets are the files that matter for EJAM installs.

## Release/version convention

Release tags in `ejamdata` should match the EJAM package/data vintage they support. For example, an EJAM package or patch release that expects `v2.32.8.001` data should use the `ejamdata` release tagged `v2.32.8.001`.

When publishing or repairing data assets:

1. Create or update the matching GitHub release tag.
2. Attach all required `.arrow` files as release assets.
3. Validate that the uploaded assets can be read by Arrow and do not contain unsafe R metadata such as `externalptr` values from `data.table` `.internal.selfref` attributes.
4. Do not assume files committed under `data/` are synchronized with release assets unless you have explicitly checked them.

## Notes on committed data files

Large `.arrow` files in this repository may be tracked with Git LFS. Removing them from the repository tree is separate from changing GitHub release assets and does not remove historical Git/LFS storage. If the repository tree is cleaned up, keep this README clear that EJAM consumes release assets, not checked-in data files.
