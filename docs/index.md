# Catalog (`shared/index.json`)

`shared/index.json` is the only catalog Salmia reads. The address on the `main` branch is:

`https://raw.githubusercontent.com/consultora-grada/salmia-releases/main/shared/index.json`

It is one JSON object. Each key is a list of packages. A missing key, or a key whose value is `[]`, means that section has nothing to offer.

Salmia shows only the list that matches the Import button. Design shows the list of the open surface.

| Key | Folder | Import button |
| --- | --- | --- |
| `presentation` | `shared/themes/presentation/` | Design, slides |
| `songbook` | `shared/themes/songbook/` | Design, songbook |
| `worship_script` | `shared/themes/worship_script/` | Design, worship script |
| `worship_order` | `shared/themes/worship_order/` | Design, order of worship |
| `songs` | `shared/songs/` | Songbook |
| `bibles` | `shared/bibles/` | Bibles |
| `images` | `shared/images/` | Images |
| `videos` | `shared/videos/` | Videos |
| `liturgies` | `shared/liturgies/` | Liturgies |

## Entry

Every item in a list has the same four fields:

| Field | Required | Role |
| --- | --- | --- |
| `id` | yes | Stable id of the entry inside that list. It is not the id stored inside the `.salmia` package. |
| `name` | yes | Name shown in the import list. |
| `description` | no | Short text under the name. Omit it, or use `""`, when there is nothing to add. |
| `downloadUrl` | yes | `https` address of the `.salmia` file. Salmia downloads this URL and then opens the same preview as a file from the computer. |

`downloadUrl` must be the raw address of the file on this repository’s `main` branch, not on a fork. Spaces and accents in the file name are percent-encoded.

```json
{
  "id": "oscuro",
  "name": "Oscuro",
  "description": "Diapositivas oscuras.",
  "downloadUrl": "https://raw.githubusercontent.com/consultora-grada/salmia-releases/main/shared/themes/presentation/Oscuro.salmia"
}
```

An empty section is an empty array:

```json
"songs": []
```
