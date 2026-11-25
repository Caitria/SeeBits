# Credits

This file mirrors the page's own **Controls → Sources & licences**
section, which is the record of record for SeeBits. Where the two ever
differ, the page's record governs.

## Author

The viewer code in `index.html` — the page, the STL parser, the shell
splitting, the print check, the WebXR / hand-tracking interaction, the VR
panels, and the scenes — is by **Caitria O'Neill** and is released under
the MIT License (see `LICENSE`), **except** for the two non-commercial
shader forks named below, which keep their own terms and are not
relabelled MIT.

SeeBits is a personal, non-commercial project. That matters for licensing:
source-available, non-commercial code may be forked in, with its exact
licence status logged here and credit kept. Nothing is relabelled MIT or
CC0 when it isn't.

## Bundled library

### Three.js — MIT

- Three.js, revision **r186**, is bundled into `index.html`. There is no
  separate library file and nothing is loaded from a CDN: the first
  `<script>` element in the page is the Three.js build inlined as a
  `data:application/javascript;base64,…` URI, which exposes a global `THREE`
  object including `GLTFLoader` (the one addon this page actually calls,
  to parse GLB files).
- The bundle carries its own licence notice at its end:

  > Bundled license information:
  > `three/build/three.core.js`, `three/build/three.module.js`
  > © Copyright 2010–2026 Three.js Authors
  > SPDX-License-Identifier: MIT

- Project: https://threejs.org/

No STL loader from Three.js is used: STL parsing (binary and ASCII) is the
author's own code in the page's second `<script>` element.

## Used in this page

| Source | What it is | Licence |
|---|---|---|
| three.js r186 (incl. GLTFLoader) | Core library — rendering, WebXR, geometry | MIT |
| Simplex noise GLSL — Ashima Arts / S. Gustavson ([webgl-noise](https://github.com/ashima/webgl-noise)) | In the sky / aurora shaders; header kept in code | MIT |
| [LYGIA](https://lygia.xyz) — Patricio Gonzalez Vivo | `generative/fbm` (rotated-matrix fbm) + `color/palette` (cosine palette), adapted as `lygiaFbm` / `lygiaPalette`; runs in the sky, aurora and arch-crystal shaders (octaves cut to 3 for Quest). Forked with credit 2026-11-22 | **Prosperity License 3.0.0 · NON-COMMERCIAL** |
| Shadertoy domain-warp technique — iq's warping / nebula lineage (density shaping as in *Protean Clouds*) | Adapted as `nebulaWarp` in the sky shader — no raymarch, sky shell only. Forked with credit 2026-11-22 | **CC BY-NC-SA 3.0 · NON-COMMERCIAL · ShareAlike applies to the adapted shader function** |
| “Rock Ground” 1K diffuse — [Poly Haven](https://polyhaven.com/a/rock_ground) | Mountain detail texture, shipped as `assets/rock_ground_1k.jpg`, wrapped around both ridge rings | CC0 (credit given per project rule; CC0 does not require it) |
| “Buddha draped in robes portraying the Realms of Existence” (the **Cosmic Buddha**) — Northern Qi dynasty, 550–577, limestone, National Museum of Asian Art (Freer Gallery of Art), Smithsonian Institution, accession **F1923.15** | 3D scan via [Smithsonian Open Access](https://3d.si.edu) (package `d8c62be8-4ebc-11ea-b77f-2e728ce88125`), built from its public-domain mirror (the 150k-face laser-scan STL); shipped as a low-resolution derivative (decimated to ~20k faces, textures removed, true size) at `assets/models/cosmic-buddha.glb` | **CC0 · public domain** |
| **MidiBitty demo model** | The author's own printed case (v0.7), six STL files in `models/midibitty/` | The author's work — MIT, like the code |
| **Planetary gear set & Geneva drive** built-ins | Generated procedurally in the page (gear / star-wheel profiles extruded as STL in memory) | Original to this page — MIT |

**Licence boundary, stated plainly:** LYGIA's Prosperity terms and the
Shadertoy CC BY-NC-SA both bar commercial use. If this viewer ever went
commercial, those two forks would need a commercial licence (LYGIA
Patron) or removal. For this non-commercial project they are in terms
as-is. A source's own explicit prohibitions still bind; nothing here
overrides them.

## Studied / not used — no code or assets from these ship in this page

- **Stone / metal PBR approach** — ambientCG (approach studied only). CC0.
- **VR panel glass recipe, flanking layout (±32°, 1.35 m) and corner-drag
  resize** — values and behaviour referenced from Meta Horizon OS Panels /
  Hands UI guidance and Apple visionOS glass principles (research report
  2026-11-22); no Meta or Apple assets, code, or components ship.
  Reference only.
- **Low-poly dressing approach** — Kenney (approach studied only). CC0.
- **Milky Way panorama** — ESO / S. Brunier, eso0932a (the band is
  re-created procedurally in the sky shader; no image file ships).
  CC BY 4.0 · credited.
- **Planet / ring textures** — Solar System Scope, based on NASA imagery
  (planet bands and rings are drawn procedurally on canvas; no texture
  file ships). CC BY 4.0 · credited.
- **Quaternius packs** — excluded (licence changed to QAL v1.0 on
  2026-08-28; CC0 spine preferred).
- **GSAP** — not used (closed-source, use restrictions); own cubic easing
  instead.

## Ideas credited in the page itself

- **Sketchfab's Model Inspector** — the inspiration for the view modes
  (Shaded / MatCap / Normals / Wireframe / Flat).
- **Meshy's viewer** — cited in the page for the same 500,000-triangle cap
  above which the manifold / print check is skipped. The Stats + Print
  Check code also mentions Manyfold's problem flags as an influence.

## Everything else

No other library, framework, font, or asset is loaded by the page: no CDN,
no analytics, no web fonts (it uses system font stacks), and no network
requests except the same-origin fetch of the built-in model files
described in `README.md` and `models/README.md`.
