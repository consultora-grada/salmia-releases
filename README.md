# salmia-releases

Distribution repository for [Salmia](https://github.com/consultora-grada/salmia). The application source code does not live here.

Salmia uses this repository in two ways: to install updates, and to offer themes the first time it runs on a computer that has none.

## App updates

GitHub Releases on this repository hold the installers. Salmia checks:

`https://github.com/consultora-grada/salmia-releases/releases/latest/download/latest.json`

People who already have Salmia then get the update from the app. They do not need to clone this repository.

## Theme catalog

`[shared/themes/index.json](shared/themes/index.json)` is the catalog Salmia reads from the `main` branch:

`https://raw.githubusercontent.com/consultora-grada/salmia-releases/main/shared/themes/index.json`

Each entry has an `id`, `name`, `description`, and `downloadUrl`. The URL points at a `.salmia` package in `shared/themes/` (today: Luminoso, Luminoso saturado, and Oscuro). On first launch, if no theme has been downloaded yet, Salmia lists those entries and imports the ones the person selects. Import uses the same path as importing a `.salmia` file from the Design window.

## Contributing a theme

Anyone can offer a theme. Write access to this repository is not required.

1. In Salmia, open Design, select the theme, and export it. That writes a `.salmia` file with the theme and the images it uses. Export only the theme, not a liturgy or a song.
2. Fork this repository and add that file under `shared/themes/`, with a short file name such as `my-theme.salmia`.
3. Add an entry to `shared/themes/index.json`: `id`, `name`, `description`, and `downloadUrl`. The URL must be the raw address on this repository’s `main` branch, not on the fork:

   `https://raw.githubusercontent.com/consultora-grada/salmia-releases/main/shared/themes/my-theme.salmia`

4. Open a pull request. After it is merged, Salmia lists the theme on first launch and imports it the same way as the themes already in the catalog.

Maintainers can push the same change directly to `main` instead of opening a pull request.





