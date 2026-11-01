# PAM-Mamba PolSAR Datasets

This repository provides the three polarimetric SAR benchmark datasets used in:

> **PAM-Mamba: Polarimetric-Prior Aligned Multi-Scale Mamba Network for PolSAR Image Classification**

Each archive contains the Lee-refined coherency matrix (T3) data and the ground-truth labels used in the experiments.

**Download:** each archive is stored in this repository as multi-part files of at most 12 MB (see [Reassembling the Split Archives](#reassembling-the-split-archives) below).

| Archive | Site | Sensor | Band | Size | Classes |
|---|---|---|---|---|---|
| `Flevoland.zip` | Flevoland, the Netherlands | AIRSAR (airborne) | L | 1024 × 750 | 15 |
| `SanFrancisco.zip` | San Francisco Bay Area, USA (SF900) | RADARSAT-2 | C | 900 × 1024 | 5 |
| `Oberpfaffenhofen.zip` | Oberpfaffenhofen, Germany | E-SAR (airborne) | L | 1200 × 1300 | 3 |

## Archive Contents

Each archive contains one dataset folder (named after the original data directory):

- `T3/` — the Lee-refined coherency matrix channels (`T11`, `T22`, `T33`, `T12_real`, `T12_imag`, `T13_real`, `T13_imag`, `T23_real`, `T23_imag`) stored as binary `.bin` files with ENVI-style `.hdr` headers, together with auxiliary polarimetric channels (`l1`, `l2`, `l3`, `lambda`) where present.
- `standard image/` — the ground-truth label file (`.mat`) and the reference color-coded classification maps:
  - Flevoland: `standard image/Farm_W.mat`
  - San Francisco: `standard image/AIRSAR_SF_W.mat`
  - Oberpfaffenhofen: `standard image/Oberpfaffenhofen_W.mat`

## Reassembling the Split Archives

Each archive is split into parts named `<archive>.zip.001`, `<archive>.zip.002`, ... Reassemble them into a single `.zip` file before extracting.

Windows (Command Prompt):

```bat
copy /b Flevoland.zip.001+Flevoland.zip.002+Flevoland.zip.003 Flevoland.zip
copy /b SanFrancisco.zip.001+SanFrancisco.zip.002+SanFrancisco.zip.003 SanFrancisco.zip
copy /b Oberpfaffenhofen.zip.001+Oberpfaffenhofen.zip.002+Oberpfaffenhofen.zip.003+Oberpfaffenhofen.zip.004+Oberpfaffenhofen.zip.005+Oberpfaffenhofen.zip.006 Oberpfaffenhofen.zip
```

Linux / macOS:

```bash
cat Flevoland.zip.* > Flevoland.zip
cat SanFrancisco.zip.* > SanFrancisco.zip
cat Oberpfaffenhofen.zip.* > Oberpfaffenhofen.zip
```

Then extract the resulting `.zip` files normally.

## Class Legends

- **Flevoland (15 classes):** Stem beans, Rapeseed, Bare soil, Potatoes, Beet, Wheat 2, Wheat 3, Wheat, Grasses, Lucerne, Peas, Barley, Forest, Water, Buildings.
- **San Francisco (5 classes):** Water, Vegetation, Bare soil, Urban, Mountain.
- **Oberpfaffenhofen (3 classes):** Built-up areas, Wood land, Open areas.

## Source

The data were derived from the following resources available in the public domain: the NASA JPL AIRSAR mission (Flevoland), the RADARSAT-2 San Francisco benchmark (SF900), and the DLR E-SAR mission (Oberpfaffenhofen).

If you use these datasets, please cite the original data sources.
