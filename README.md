# SeeBits

**See the bits of your model.** SeeBits inspects your own 3D-print files —
**STL and GLB** — at **true 1:1 size**, in 2D on a phone or desktop and in
VR on a Meta Quest, so you can hold a part in your hands and check it
*before* it prints.

- **Free, browser-only.** One web page. No install, no account, nothing to
  sideload.
- **Your files never leave your device.** Everything is parsed and rendered
  locally in your browser; the page uploads nothing.
- **Live:** https://caitriaoneill.com/seebits (the same page also answers
  at https://caitriaoneill.com/vr)

![status](https://img.shields.io/badge/single%20file-index.html-brightgreen)

## Why

Checking a 3D-print design on a flat screen lies to you about the things
that matter most before a print: how big it actually is, whether two shells
really clear each other, whether a cap will feel chunky or delicate in your
hand, and whether the assembled thing reads as one object. SeeBits exists
because its author wanted to hold a case she was designing and pull it
apart before paying for another failed print. The workflow it serves:

1. **Idea** — sketch it, measure the real thing it must fit.
2. **Model** — describe the shape in code (the original workflow used
   OpenSCAD), every dimension a number you can change.
3. **STL / GLB** — export, parts in assembled coordinates.
4. **SeeBits** — load the files here and check fit and scale at true 1:1
   **before anything prints**.

## How to use it

### Phone or desktop

1. Open https://caitriaoneill.com/seebits — or serve this repo's
   `index.html` yourself (see [Run it / host it](#run-it--host-it)).
2. **Load your file:** tap **📂 Load file** and pick one or more `.stl` /
   `.glb` files, or drag and drop them anywhere on the page. A built-in
   model (the MidiBitty demo) is there first so the page is never empty.
3. **Look around:** drag to orbit, pinch or scroll to zoom, two-finger drag
   or right-drag to pan. Tap a part to select it.
4. **Pull it apart:** the **Apart** slider in the bottom bar fans a
   multi-part model out into a separated stack and back.
5. **Switch the scene:** the **[Cyber | Galaxy]** switcher sits beside the
   Apart slider, always visible — Cyber is the plain empty Tron-style
   void, Galaxy is the cosmos scene.
6. **Everything else is in ☰ Tools**, in three tabs:
   - **Parts** — the part list (searchable, grouped — see below), grab
     mode, Apart direction.
   - **Measure & Fit** — dimensions and print check, the Measure tool,
     the Section cut, units, and fit pointers for your printer and
     material.
   - **Look** — the five view modes, environment light, VR height,
     recenter, and the link to the full Controls reference.
7. **↺ Reset** (bottom bar) restores the model exactly as it loaded.

### Quest headset

Files are picked in the flat browser panel *before* entering VR — a WebXR
session cannot open a file picker.

1. Get your file into the headset's **Downloads** — via Quest Browser, the
   Files app (Google Drive), or USB into the Download folder.
2. Hold the **Meta button** → open the **apps grid** → tap **Browser**
   (globe icon) → go to **caitriaoneill.com/seebits**. Stay in the flat 2D
   panel.
3. Tap **Choose your file**; in the picker, go to **Downloads** and pick
   your STL or GLB.
4. Check the model is on screen, then tap **🥽 Enter VR** in the bottom
   bar.
5. In VR the model is straight ahead at true size. Three controls float
   low by the model's base and are always there: the **Apart slider**, the
   **Mode pill** (Cyber | Galaxy), and **↺ Reset**. The **Parts & Layers**
   panel sits at your left and **Tools & Settings** at your right — a
   **quick pinch in empty air** hides them or brings them back. Pinch-hold
   a part to grab, move, and twist it; two hands pinch-holding scale and
   turn together.
6. **EXIT VR** is on the right-hand panel (quick-pinch brings the panels
   back if they're hidden) — or press **B** / **Y** with controllers, or
   use the left-palm Meta pinch-and-hold for the system menu.

Known snag, from the page's own guide: a Quest Browser bug can refuse a
picked file (access-denied; reported for .glb). If that happens it's the
bug, not your file — the built-ins always work, or load the file on
phone/desktop first.

## What it does

- **True scale, always.** A 46 mm part is 46 mm, on screen and in the
  headset. A badge shows the model's bounding box in mm at all times.
- **Apart slider** — fans parts out from the model's base along the
  assembly axis (Vertical), the longest axis (Horizontal), or both
  (Mixed), with trail lines back to the assembled pose. Parts never sink
  below the surface the model rests on. A single solid has nothing to
  separate, and the slider says so instead of sitting there looking
  broken.
- **Parts that scale to real assemblies.** Each STL becomes one part per
  connected shell inside it; a GLB brings its own named parts. The Parts
  tab groups parts (by source file, finish, or name), collapses groups by
  default with counts, and has search plus Shown / Ghosted / Hidden
  filters — a 19-part demo and a 120-part GLB stay navigable. Selecting a
  part in 3D scrolls its row into view. Isolate ghosts everything else;
  Unisolate restores exactly the visibility you had before.
- **Colour and finish, per part.** Tap a part and the bar that appears
  carries its colour swatches, a custom colour, and a finish — Opaque
  gloss, Opaque matte, or Translucent (transparent-PETG-like) — to mock up
  the physical build. Saved per part name in your browser.
- **Measure & Fit.** Dimensions, triangles, vertices, volume, surface
  area, and a manifold / watertight check (skipped, and labelled as
  skipped, above 500,000 triangles). The Measure tool takes two taps;
  label what you measured — Gap / Hole / Peg / Wall — and the fit verdict
  uses bands for your printer and material (PLA, PETG, ABS/ASA, TPU,
  resin). Pointers appear only when this model trips one — a dimension
  over your printer's build volume, a likely inches-instead-of-mm STL, a
  non-manifold mesh with its open-edge count — each with the evidence, a
  judgement, and one next step. One honest limit, stated in the tab: wall
  thickness and overhangs are *not* measured here. **Your slicer is still
  the authority.**
- **Section slider** — slice the model open with a clipping plane.
- **Five view modes** (keys 1–5): Shaded, MatCap, Normals (exposes flipped
  faces), Wireframe, Flat — the Sketchfab Inspector idea, adapted.
- **Two scenes, genuinely different places.** **Cyber:** an empty Tron
  void — grid floor, light ring, the model, nothing else. **Galaxy:**
  cosmos only — drifting stars and nebulae, a ringed planet with an
  orbiting moon and companion worlds, tiny soft-glow sparkles; no ground,
  so nothing can ever hide a part of the model. The switcher is always
  visible; your choice is remembered between visits.
- **Grab the way you expect.** Whole-model grab is the default — a first
  grab can never pull one layer out of an assembly by accident. Single-part
  grab is one explicit toggle away. In VR everything is hands-first;
  controllers map to the same actions.

## Run it / host it

The viewer is one static page. Any static HTTPS host works: GitHub Pages,
Netlify, Cloudflare Pages, a plain web server.

```text
index.html            ← the whole app (about 3.9 MB — Three.js and the
                        viewer's own code, inlined; no build step, no CDN)
models/midibitty/     ← the built-in demo's STL files (see models/README.md)
```

1. Copy `index.html` and the `models/` folder to your host.
2. Serve over **HTTPS**. WebXR requires a secure context; on an insecure
   page the Enter VR / AR buttons disable themselves and say so.
3. On the Quest: open the URL in **Quest Browser** and follow the
   [headset steps](#quest-headset).

No account, no install. On a desktop or phone browser the same page is a
fully usable flat viewer.

## Models: three ways in

### 1. Load your own (no code change)

- Drag and drop `.stl` or `.glb` files anywhere on the page, or use
  **📂 Load file** and pick several at once — multiple files load as one
  assembly.
- Each STL becomes **one part per connected shell** inside it, numbered
  (`Name · 1`, `Name · 2`, …, largest first), so it can be pulled apart
  part by part. (The split is skipped above 1,000,000 triangles.)
- A GLB brings **its own named parts**, at its own coordinates.
- Export parts in **assembled pose**: parts keep the coordinates they were
  exported at, so an assembly exported in place arrives assembled.
- **Units and scale.** The scene is metres; model geometry is held in
  millimetres and scaled ×0.001, so models display at true 1:1.
  - *STL carries no units.* STL coordinates are treated as **millimetres,
    Z-up**. If your STL is in inches, use **Tools → Measure & Fit →
    Units**: **Inches → mm (×25.4)**. GLB is unaffected by that toggle.
  - *GLB/glTF is always metres, Y-up* in the format; the loader converts
    it at exactly ×1000 into the viewer's Z-up millimetre frame.
  - Part names for STL come from the filenames (extension stripped,
    `_`/`-` become spaces, words capitalised). GLB parts keep their node
    names.

### 2. Built-in models (no files of yours)

The built-in dropdown loads four models, all reachable from inside a
headset:

- **MidiBitty — Demo** (the default): a real printed case — the author's
  own MidiBitty v0.7 — as six STL files whose shells split into 19 parts
  in the list. File-based: see [models/README.md](models/README.md). Also
  loads from `?sample=midibitty`.
- **Planetary gear set** and **Geneva drive**: generated procedurally in
  the page (gear / star-wheel profiles extruded as STL in memory) — no
  files, always work. Original to this page. `?model=planetary`,
  `?model=geneva`.
- **Cosmic Buddha — Smithsonian (CC0)**: “Buddha draped in robes
  portraying the Realms of Existence,” Northern Qi dynasty, 550–577,
  Freer Gallery of Art, Smithsonian Institution (accession F1923.15),
  via Smithsonian Open Access. The page carries a low-resolution
  derivative (decimated to ~20k faces, textures removed, true size).
  `?model=cosmic-buddha`.

### 3. Your own files as the built-in sample

There is **no manifest file and no config** — the MidiBitty set is
registered in code, in `index.html`:

1. **Export** one STL per part (binary or ASCII), in assembled
   coordinates, millimetres, Z-up.
2. **Place the files** in `models/midibitty/` next to `index.html`, using
   these filenames — or edit the `SAMPLE_FILES` array in `index.html`
   (search for `SAMPLE_FILES`) to list yours instead:

   ```text
   models/midibitty/back_shell.stl
   models/midibitty/front_face.stl
   models/midibitty/panel_insert.stl
   models/midibitty/diffuser_insert.stl
   models/midibitty/grille_insert.stl
   models/midibitty/caps_set.stl
   ```

   (`assets/models/midibitty/` is tried as a fallback path.) The loader
   fetches every listed file, validates all of them — response OK, at
   least 200 bytes, first byte not `<` (which would mean an HTML error
   page) — and only then replaces the model on screen, so a missing file
   never destroys the current view. Part labels derive from the
   filenames, so name files the way you want parts labelled.
3. **Serve over HTTPS** and pick the MidiBitty demo, or open
   `your-host/seebits/?sample=midibitty`.

Loading arbitrary models at run time never needs any of this: use
drag-and-drop or **Load file**.

## Controls

### Phone & desktop

| Input | Action |
|---|---|
| Drag | Orbit around the model |
| Pinch / scroll wheel | Zoom |
| Two-finger drag / right-drag | Pan |
| Tap / click a part | Select it (highlight + name; its colour/finish controls appear in the bar above the bottom bar) |
| **Apart** slider (bottom bar) | Fan the parts out into a separated stack, 0–100%, with trail lines back to the assembled pose |
| **[Cyber \| Galaxy]** switcher (bottom bar, always visible) | Switch scene; the active side is filled |
| **Section** slider (Tools → Measure & Fit) | Slice the model open with a clipping plane (100% = off) |
| **Measure** (Tools → Measure & Fit) | Tap two points — distance in mm, with a fit verdict once you label it Gap / Hole / Peg / Wall |
| Keys **1–5** | View modes: 1 Shaded · 2 MatCap · 3 Normals · 4 Wireframe · 5 Flat |
| Key **I** | Toggle the Tools drawer |
| **☰ Tools** | The three tabs: Parts · Measure & Fit · Look |
| **🥽 Enter VR** / **🏠 View in your room** | Start an immersive-vr / immersive-ar WebXR session (disabled, with an explanation, if the browser reports no support) |
| **↺ Reset** | Restore everything to the moment the file loaded: part positions and rotations, Apart 0%, section cleared, hidden/ghosted parts, colours/finishes, grabs undone, view/home restored. It does not reload the file |
| Esc | Exit an XR session |

In **Tools → Look** you also get: environment light (**Studio** · **Bench**
with a 10 mm grid · **Dark** headlamp), VR height (**Seated** ≈ 1.0 m
model centre, the default · **Standing** ≈ 1.35 m), **Recenter**, and the
**Controls, sources & licences** reference.

### In the headset (Quest) — hands first

Hand tracking is the primary input. A WebXR *select* event is both a
controller trigger pull **and** a thumb-to-index pinch, and every action
below is wired to it, so hands and controllers are interchangeable.

| Gesture / input | Action |
|---|---|
| Quick pinch on a part | **Select it** — a quick pinch is a tap |
| Pinch a part **and hold**, then drag | **Grab**: dragging moves it, twisting your wrist rotates it. Release to let go. The grab activates once your hand has moved ~15 mm, so a quick pinch never becomes a grab by accident |
| Pinch-hold, **Grab mode: Whole model** (default) | A pinch-hold on any part carries and wrist-twists **all parts together as one rigid model** |
| Two hands, **both pinching**, spread / bring together | Scale and turn the same target (the scale is an inspection scale — the page distinguishes it from true 1:1 and offers a reset when you've scaled) |
| Quick pinch in **empty air** | **Hide or bring back the two flank panels**. VR starts with the panels up: Parts & Layers at your left, Tools & Settings at your right, nothing in front of your face. If a panel is lost, the pinch re-places both at your flanks |
| Floating **Apart** pill | Pinch-hold its track and drag — it *is* the slider (drag to 0 to re-assemble) |
| Floating **Mode** pill | Switch Cyber \| Galaxy without opening any panel |
| Floating **↺ Reset** pill | Restore the model exactly as loaded |
| Drag a panel or pill by its **dotted grip** | Move it; it stays where you drop it, world-locked, and the spot is remembered between visits. Pinch a panel's corner bracket to resize it |
| Panel buttons (pinch them) | LOAD (the four built-ins), the selected part's state and colour/finish, grab mode, Show all, Reset model, and the red **EXIT VR** |
| Controller grip in empty air | Grab the world and pull it around you — clamped near its home spot so it cannot be thrown out of reach. With hands, Reset recovers the model's position instead |
| Leave VR / AR | Pinch the red **EXIT VR** button on the right panel (quick-pinch in empty air brings the panels back first); or look at your **left palm** and pinch-and-hold the Meta icon for the system menu; with controllers, **B** (right) / **Y** (left) at any time, or the Meta button → Quit |

Other in-headset behaviour worth knowing:

- Your hands render as **ghost hands** — very faint joint dots and bone
  lines, theme-tinted — so you can see where your hands are without them
  ever covering the model.
- Galaxy keeps its ambient sparkles **out of the corridor between your
  face and the model/panels**, so the view of the part stays clean.
- Panel text is drawn supersampled (3× canvas) so it stays sharp at arm's
  length.

## How it works

All of this is in the single `index.html`. Structurally it is two
`<script>` elements: Three.js r186 inlined as a base64 data URI, and the
viewer's own code (including its own STL parser — no STL loader is used).

- **WebXR session setup.** Buttons first ask
  `navigator.xr.isSessionSupported("immersive-vr" | "immersive-ar")` and
  disable themselves if unsupported. Starting a session requests
  `local-floor` / `bounded-floor` reference spaces, and for the session the
  camera's near/far planes are swapped from desktop values to
  0.01 m / 60 m and restored when the session ends.
- **Placing the scene from the real head pose.** Nothing is placed at
  `sessionstart` — no viewer pose exists yet, and placing then strands the
  model at the floor origin. Instead the render loop waits for a few
  presenting frames, reads the real head pose, flattens its direction to
  the horizontal, and places the world from it: the model straight ahead
  at the height for the Seated/Standing setting, flank panels at about
  ±32° and 1.35 m out, floating pills low at the sides of the model's
  base. If no head pose arrives after ~90 frames (~1.5 s), it falls back
  to a sane local-floor default rather than the origin.
- **World-locked model, true scale.** The hierarchy is
  `worldGroup → spinGroup → modelGroup`; `modelGroup` is scaled ×0.001
  (mm → m) and rotated −90° about X (STL Z-up → world Y-up). Once placed,
  the model, panels, and pills are **world-locked**: they stay where they
  were put while you walk around them, giving real parallax.
- **Supersampled panel textures.** In-headset panels are drawn on 2D
  canvases at **3× their logical resolution** and used as
  `THREE.CanvasTexture`s with maximum anisotropy and linear-mipmap
  filtering. That is what makes panel text sharp at arm's length instead
  of fuzzy. Hit-testing maps the controller/hand ray's UV on the panel
  plane back into the same logical coordinates as the drawn button
  regions.
- **Pinch handling.** Both controllers are obtained with
  `renderer.xr.getController(i)`; a `connected` event records whether the
  input source is a hand, so a pinch is never also treated as a squeeze.
  `selectstart` / `selectend` carry every tap, panel button, and grab.
  Timing separates the gestures: a pinch released within **320 ms** is a
  tap / panel toggle; a held pinch on a part becomes a grab once the hand
  moves ~15 mm. Because one Quest pinch can report as *both* a select and
  a squeeze, squeeze events arriving while the pinch is down (or in a
  short race window around it) are recognised as that same pinch and
  suppressed, so a pinch never accidentally world-grabs the scene away.
- **Explode (Apart) implementation.** Parts are *ordered* along an axis by
  their centre's signed distance from the assembly centre, then, at 100%,
  laid end to end along that axis with a clear gap between every pair of
  bounding boxes. Ordering — not distance from the centre — sets the
  spacing, so nested shells that share almost the same centre (the common
  case for a printed case) still separate cleanly. The slider value
  multiplies each part's computed offset, and trail lines are drawn from
  each part's assembled centre to its exploded centre. Parts are clamped
  so they never sink below the surface the model rests on.
- **The two scenes.** Cyber and Galaxy are different constructions, not
  one scene recoloured — see the page's own Controls → Sources & licences
  for the construction notes, budgets, and the exact licence status of
  every shader source used. Galaxy has no ground at all: the workbench
  terrace an earlier version had was removed after a headset session
  showed an opaque shelf hiding grabbed parts.
- **Persistence.** Scene choice, per-part appearances, panel/pill
  positions and sizes, VR height, and Measure & Fit's printer/material
  choices are kept in `localStorage`. Models you load are parsed in memory
  and never stored or uploaded by the page.

## Verification status

Stated plainly, because the page's own record states it plainly: the 2D
experience — loading, tabs, grouping, Measure & Fit, the switcher — is
verified, including headless rendered checks of the current build. The VR
floating **Mode pill** (new in the Nov 25, 2026 simplification) and the
two-tap **Measure fit callouts** have not yet been verified in a headset
session; the Quest session is the verdict there. Scene performance figures
quoted in the page's Sources section are documented budgets, not
measurements of this viewer.

## Limitations

- **WebXR needs a secure context and a capable browser.** In practice:
  Quest Browser over HTTPS for VR/AR and hand tracking. Desktop browsers
  get the flat viewer; Safari without WebXR gets the flat viewer only.
- **No file picker inside a headset** — a WebXR session cannot open the
  Quest file system, which is exactly why the built-ins are loadable from
  the VR panel and your own files are loaded in 2D first.
- **Performance caps, by design:** the manifold check is skipped above
  500,000 triangles (stats still compute), and shell-splitting is skipped
  above 1,000,000 triangles. Very large STLs still load, but as a single
  part per file.
- **glTF with external resources:** the loader is handed the file's own
  buffer with an empty resource path, so a self-contained **.glb** is the
  reliable form; a `.gltf` that references separate texture/buffer files
  has nothing to resolve them against.
- **Scale is only as true as your export.** The viewer trusts STL
  coordinates as millimetres; an STL exported in inches will appear
  25.4× too small until you flip the Units toggle — Measure & Fit's
  pointers will also flag a suspiciously small STL and offer the
  conversion.
- **Appearances and settings are per-browser.** They live in that
  browser's local storage — clearing site data removes them, and they do
  not follow you between the desktop and the headset.
- The page is a **viewer, not a slicer**: no supports, no repair, no
  export. The print check is a heuristic second opinion; your slicer is
  the authority.

## Variations to try

- **Your own sample set** — the fastest fork: swap the six files in
  `models/midibitty/` (or edit `SAMPLE_FILES`) and the headset-loadable
  demo becomes your product, your enclosure, your classroom handout.
- **A gallery page** — host several copies of the folder with different
  sample sets and link them; `?sample=midibitty` and `?model=…`
  deep-link straight into a built-in on load.
- **Different built-in mechanisms** — `makePlanetaryFiles()` /
  `makeGenevaFiles()` show the pattern for procedural, zero-network
  models: build geometry, rotate it into the STL frame (Z-up, mm),
  serialise with the page's STL writer, and feed it through `loadFiles()`.
- **Classroom / review kiosk** — because it is one static file, it can be
  hosted per-course or per-team with that group's sample parts, and used
  with controllers instead of hands wherever hand tracking is impractical.

## Licence

- **This project's own code** (the viewer's code in `index.html`, this
  README, the MidiBitty demo model) is **MIT** — see
  [`LICENSE`](LICENSE). Copyright (c) 2026 Caitria O'Neill.
- **Bundled Three.js r186** is under **its own MIT licence**, carried in
  the bundle. See [`CREDITS.md`](CREDITS.md).
- **Model assets keep their own terms.** The Cosmic Buddha is **CC0 /
  public domain** (Smithsonian Open Access). The MidiBitty demo is the
  author's own work, MIT like the code.
- **⚠️ Not everything in the page is MIT.** Two shader sources are forked
  under **non-commercial** terms — **LYGIA** (Prosperity License 3.0.0)
  and a **Shadertoy-derived** domain-warp technique (**CC BY-NC-SA 3.0**,
  ShareAlike applies to the adapted shader function). They are in terms
  for this personal, non-commercial project; **they are not relabelled
  MIT**, and a commercial fork of this page would need a commercial
  licence for LYGIA (Patron) or removal of both. Full details, and every
  other source, are in [`CREDITS.md`](CREDITS.md) and in the page's own
  Controls → Sources & licences — the record of record.
