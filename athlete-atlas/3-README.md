# Athlete Atlas

A working injury-evidence explorer and original interactive anatomy prototype.

## Run and build

Requires Node.js 20 or newer.

```sh
npm ci
npm run build
# dist/muscles.bin is generated from BodyParts3D sources (CC BY 4.0); the built copy is included
python -m http.server 8080 -d dist
```

Open http://localhost:8080. Deploy the contents of `dist/` to GitHub Pages or any static host. The prebuilt `dist/` is included. There is no backend, account setup, API key or paid dependency. No information is transmitted by the app; external research links open separately. Choices are temporary page state.

## Working features

- HYROX, cricket, badminton, running, football, basketball, tennis, volleyball, swimming and cycling. This is prototype coverage, not a popularity ranking.
- Sport-specific role/event filters and a separate fictional gender-group demo.
- Animated geometric hero mark, scrolling sport selector and a three-question routine/pain intake. Answers stay in temporary page state on the device; nothing is transmitted. Reported pain is a distinct, clearly labeled map mode, separate from published and fictional data.
- Source-backed HYROX regional episode counts, unavailable states for unsupported subsets and a distinctly labeled synthetic dataset.
- Clickable front/back anatomy plus a rotatable 3D muscular/skeletal view built from BodyParts3D meshes (CC BY 4.0, see THIRD_PARTY_LICENSES.txt), zoom, pause/motion and a bone layer. It is an orientation aid, not a diagnosis tool.
- Region details, previous-injury evidence notes, supervised conditioning examples and rehab boundaries.
- Keyboard-accessible regional buttons, arrow-key orbit and reduced-motion support.

## Data and safety

The published map transcribes Table 3 of Chittenden et al. (2026), DOI 10.3389/fspor.2026.1937574. It combines acute and overuse counts for each named region: 55 mapped episodes plus 8 other/unspecified = 63. Denominator: all injury episodes, not athletes, and not only HYROX-attributed injuries. Both sides share one region count. No laterality or gender-by-region/role-by-region breakdown is inferred.

No clinical prediction model is trained or deployed. Previous injury changes evidence notes, never counts. Gender identity is not treated as study-recorded sex. A zero count does not imply safety. No diagnosis, personal injury probability, rehabilitation prescription or return-to-play clearance is generated. Real use needs clinical and privacy governance, consent, standardized longitudinal data and independent validation.

## Asset and software provenance

All vector/procedural geometry and interface source in this project were authored for this prototype. No Sketchfab/MSD assets, textures or viewer code were copied. They were interaction references only. No third-party exercise illustrations were copied. Research and AAOS sources are linked in the app; exercise examples are brief paraphrases for clinician discussion.

React and React DOM are MIT-licensed. esbuild is MIT-licensed. Their license files are included in THIRD_PARTY_LICENSES.txt. This project uses its own portable UI components and system fonts.

## Sources

See `src/data.ts` for the complete curated source ledger and per-source caveats. Research checked 12 November 2026.

## Single-file build

`node build-single.mjs [mesh-name]` writes `dist/index-single.html` (CSS and JS inlined). The live GitHub Pages copy is built with `node build-single.mjs 8-muscles.bin` because the mesh file there is named `8-muscles.bin`.

## Change log (parity with the live site, 2026-11-12)

- Questionnaire gate now compares the pain answer to the real option values ("No pain" / "Yes - mark where"), so the anatomy view opens once all three questions are answered.
- 3D meshes are copied into aligned per-part GPU buffers (the file offsets in `muscles.bin` are not 2-byte aligned).
- Joint markers are positioned from the mesh bounds so they sit on the limbs.
- Exercises are a full-width section below the anatomy and region detail, not a hidden tab.

## Change log (2026-11-12, data loader)

- New "Load data / Use your own dataset" section: load a CSV or JSON file with a region column (region / body_part / location), optional sport and count columns. Counts are mapped to the 12 atlas regions and drive the anatomy map as a fourth, clearly labeled "Loaded data" view, separate from published, fictional and pain layers. Parsing is fully on-device (src/parseData.ts); nothing is uploaded.
- Kaggle Multimodal Sports Injury Dataset (anjalibhegam, CC BY-NC-SA 4.0) included as a summary layer: counted from the CSV on 12 Nov 2026 (15,420 sessions, 156 athletes; Healthy 9,868, Low Risk 3,238, Injured 2,314). It has no body-region field, so it is shown as per-sport session rates and never colours the map. Uploading the Kaggle CSV itself is detected and summarised the same way.
