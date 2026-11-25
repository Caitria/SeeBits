# The `models/` folder

This folder holds the one file-based built-in set in SeeBits: the
**MidiBitty demo** — a real printed case (the author's own MidiBitty v0.7)
in six STL files, in exactly this layout, next to `index.html`:

```
index.html
models/
  midibitty/
    back_shell.stl
    front_face.stl
    panel_insert.stl
    diffuser_insert.stl
    grille_insert.stl
    caps_set.stl
```

The six files **are included in this repository** (they are the author's
own work, MIT like the code — see the main README's Licence section).
Their shells split on load into 19 parts in the Parts list.

The other built-ins need no files here:

- **Planetary gear set** and **Geneva drive** are generated procedurally
  in the page (gear / star-wheel profiles extruded as STL in memory).
- **Cosmic Buddha — Smithsonian (CC0)** is carried in the page itself as a
  low-resolution derivative of the Smithsonian Open Access scan (see
  `CREDITS.md`).

## How the MidiBitty set is registered

That list is not discovered by scanning the folder. It is hard-coded in
`index.html`, in the `SAMPLE_FILES` array:

```js
var SAMPLE_FILES = ["back_shell.stl", "front_face.stl", "panel_insert.stl",
                    "diffuser_insert.stl", "grille_insert.stl", "caps_set.stl"];
```

The code fetches `models/midibitty/<filename>` for each entry — and, as a
fallback for a differently-shaped deployment, `assets/models/midibitty/<filename>`.
All six must arrive before anything is replaced on screen: a failed fetch
leaves the current model untouched, and each response is rejected if it is
not `ok`, is under 200 bytes, or starts with `<` (an HTML error page served
in place of an STL). If the set can't load at first boot, the page falls
back to a procedural built-in rather than leaving an empty scene.

## Dropping in your own files as the built-in demo

1. Export one STL per part, in **assembled coordinates** (parts at the
   positions they occupy in the finished assembly, not laid out on a print
   bed). Units are **millimetres, Z-up** — STL carries no units, and the
   viewer treats STL coordinates as mm unless the Inches unit toggle is
   selected (×25.4). Either binary or ASCII STL works; the page has its
   own parser for both.
2. Put the files in `models/midibitty/`, using the six filenames above —
   **or** edit `SAMPLE_FILES` in `index.html` to list your filenames
   instead, keeping the files in that same folder. Part names shown in the
   UI are derived from the filenames (extension stripped, `_` / `-` become
   spaces, words capitalised), so name the files the way you want the
   parts labelled.
3. Serve the folder over HTTPS (see the main README) and pick the
   MidiBitty demo, or open the page with `?sample=midibitty`.

Notes:

- A single STL that contains several disconnected solids is split on load
  into one part per connected shell (named `Name · 1`, `Name · 2`, …,
  largest first), so a multi-shell file still pulls apart, ghosts, and
  isolates part by part. The split is skipped for meshes over 1,000,000
  triangles.
- There is no manifest file: adding a differently-named hosted set means
  editing `loadMidiBitty()` / `fetchSampleSet()` in `index.html` (fetch
  path, file list, and labels), not just adding a folder. Loading arbitrary
  models at run time needs no code change at all — use the page's
  **Load file** button or drag-and-drop instead.
