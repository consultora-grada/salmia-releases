# salmia-releases

Distribution repository for [Salmia](https://github.com/consultora-grada/salmia). The application source code does not live here.

Salmia uses this repository in two ways: to install updates, and to share `.salmia` packages that a person can import from inside the app.

## App updates

GitHub Releases on this repository hold the installers. Salmia checks:

`https://github.com/consultora-grada/salmia-releases/releases/latest/download/latest.json`

People who already have Salmia then get the update from the app. They do not need to clone this repository.

## Catalog

`shared/index.json` is the only catalog Salmia reads from the `main` branch:

`https://raw.githubusercontent.com/consultora-grada/salmia-releases/main/shared/index.json`

Each list matches the Import button that opens it. An entry has an `id`, `name`, `description`, and `downloadUrl`. The URL points at a `.salmia` file in that list's folder. The format is described in [docs/index.md](docs/index.md). From Import, then “From the Salmia repository”, Salmia shows only that list. An empty list says so. Choosing an entry downloads the package and opens the same preview as a file from the computer.

Themes live under `shared/themes/`:

- `presentation` — slide themes
- `songbook` — songbook PDF themes
- `worship_script` — worship script themes
- `worship_order` — order of worship themes

The other lists are the shared library:

- `songs` — songbook
- `bibles` — bibles
- `images` — images
- `videos` — videos
- `liturgies` — liturgies

GitHub rejects a file over 100 MB and warns from 50 MB.

## Legal notice

Publishing a resource in this repository requires that you hold every legal right needed to share it. That includes copyright and any other intellectual property in the text, music, images, video, and any other material inside the package. Do not submit work you are not allowed to distribute.

If you believe a file here infringes your legal rights or your intellectual property, send a claim to carlos.jacobs@grada.com.ar. Name the file, the right you say is affected, and how to reach you.

## Contributing

Anyone can offer a resource. Write access to this repository is not required. By submitting a file you confirm the legal notice above.

1. In Salmia, open Design, select the surface (slides, songbook, script, or order of worship), select the theme, and export it. That writes a `.salmia` file with that theme and the images it uses. Export only the theme, not a liturgy or a song.
2. Fork this repository and add that file under the matching folder in `shared/themes/`, with a short file name such as `my-theme.salmia`.
3. Add an entry to the matching list in `shared/index.json`: `id`, `name`, `description`, and `downloadUrl`. The URL must be the raw address on this repository’s `main` branch, not on the fork:
  `https://raw.githubusercontent.com/consultora-grada/salmia-releases/main/shared/themes/presentation/my-theme.salmia`
4. Open a pull request. After it is merged, the theme appears under Design → Import → From the Salmia repository, on that surface.

The same steps publish a song, bible, image pack, video, or liturgy. Export a `.salmia` from the matching screen, put the file in `shared/songs/`, `shared/bibles/`, `shared/images/`, `shared/videos/`, or `shared/liturgies/`, and add the entry to that list in the same `shared/index.json`. The raw URL uses this repository’s `main` branch. Import from that screen then offers the package.