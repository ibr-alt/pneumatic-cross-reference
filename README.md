# Pneumatic part-number and size reference data

Supplier-maintained, openly licensed reference data for industrial pneumatic cylinders.
The checked snapshot contains **61 cross-reference pairs** from **Festo (4), SMC (19), AirTAC (20) and Camozzi (18)** to a WAALPC candidate size, with bore and stroke in millimetres and a reference page for each candidate.

## Download

- [Checked CSV, 16 November 2026](checked/2026-11-16.csv) — UTF-8, comma-separated, one pair per row, no login.
- [Provenance and SHA-256](checked/2026-11-16.provenance.json) — core row identifiers, source fingerprints and verification criteria.
- [License](LICENSE) — Creative Commons Attribution 4.0 International (CC BY 4.0).

The 61 pairs link to **59 distinct size-reference pages** on [corneta.tech](https://corneta.tech/analog/). All 59 addresses returned HTTP 200 at their canonical URL when checked on 16 November 2026. Repeated candidate sizes are intentional: different foreign part numbers can lead to the same candidate.

## What a row means

`relation=size_candidate` records a candidate with the stated bore and stroke. It does **not** certify a drop-in replacement, manufacturer approval, or identical mounting, rod end, port thread, cushioning, sensors, pressure or temperature limits. Check the two manufacturers' drawings and specifications before substitution. The reference website is operated by the dataset supplier and contains commercial product pages; the CSV itself contains no prices, availability or delivery times.

Part numbers are strings: preserve punctuation, leading zeros and letter case. Numeric Festo ordering identifiers are valid strings too. `bore_mm` and `stroke_mm` refer to the WAALPC candidate. There are no negative pairs, evaluation splits or measured matching-accuracy claims.

## Schema

| Column | Meaning |
|---|---|
| `brand` | Manufacturer of the foreign part number. |
| `alien_code` | Foreign part number, preserved from the source. |
| `waalpc_code` | Exact WAALPC candidate SKU. |
| `bore_mm` | Candidate bore in millimetres. |
| `stroke_mm` | Candidate stroke in millimetres. |
| `relation` | `size_candidate`; no automatic physical-interchangeability claim. |
| `reference_url` | Canonical candidate page on corneta.tech. |
| `checked_on` | Snapshot check date, ISO 8601. |

## Source and verification

This is a dated, read-only export of the shared `wp_cv2_analog_index` source, not an independently maintained mapping database. Updates must be generated from that source again; do not hand-edit correspondences in this repository.

Every included pair met all of these checks:

1. The latest fact-check decision for the exact brand, foreign code and WAALPC SKU was approved, with an identified catalog basis.
2. The exact pair was present in the live core with `verified=1` and a level other than the search-only `poisk` level.
3. The exact candidate SKU existed in the SKU registry; its bore and stroke agreed with the core; its parent product was published.
4. Its reference URL passed the live HTTP, canonical URL and candidate-code checks. Protected experiment/control addresses and unsuccessful URL checks were excluded.

The core's `verified` flag alone was not treated as proof of a catalogued foreign code or of full interchangeability. The provenance file records the supporting core IDs and the fact-check source fingerprint; private operational notes and credentials are not distributed.

## Use

The CSV can be used as reference input for spare-parts identifier reconciliation, catalog normalization and manual candidate-size lookup. It is a small supplier-selected sample, not an exhaustive manufacturer catalog or a validated machine-learning benchmark.

```python
import csv
from pathlib import Path

with Path("checked/2026-11-16.csv").open(encoding="utf-8", newline="") as stream:
    rows = list(csv.DictReader(stream))

matches = [row for row in rows if row["brand"] == "SMC"]
```

## Checked pairs

| Brand | Foreign code | WAALPC candidate and reference page | Bore × stroke, mm |
|---|---|---|---|
| AirTAC | `SDA20X30B` | [SDA-20-30-P-A](https://corneta.tech/pnevmocilindr-sda/sda-20-30-p-a/) | 20 × 30 |
| AirTAC | `SDA20X40B` | [SDA-20-40-P-A](https://corneta.tech/pnevmocilindr-sda/sda-20-40-p-a/) | 20 × 40 |
| AirTAC | `SDA20X80` | [SDA-20-80-P-A](https://corneta.tech/pnevmocilindr-sda/sda-20-80-p-a/) | 20 × 80 |
| AirTAC | `SDA25X10B` | [SDA-25-10-P-A](https://corneta.tech/pnevmocilindr-sda/sda-25-10-p-a/) | 25 × 10 |
| AirTAC | `SDA25X70B` | [SDA-25-70-P-A](https://corneta.tech/pnevmocilindr-sda/sda-25-70-p-a/) | 25 × 70 |
| AirTAC | `SDA25X80` | [SDA-25-80-P-A](https://corneta.tech/pnevmocilindr-sda/sda-25-80-p-a/) | 25 × 80 |
| AirTAC | `SDA32X100` | [SDA-32-100-P-A](https://corneta.tech/pnevmocilindr-sda/sda-32-100-p-a/) | 32 × 100 |
| AirTAC | `SDA32X25` | [SDA-32-25-P-A](https://corneta.tech/pnevmocilindr-sda/sda-32-25-p-a/) | 32 × 25 |
| AirTAC | `SDA50X100` | [SDA-50-100-P-A](https://corneta.tech/pnevmocilindr-sda/sda-50-100-p-a/) | 50 × 100 |
| AirTAC | `SDA50X10B` | [SDA-50-10-P-A](https://corneta.tech/pnevmocilindr-sda/sda-50-10-p-a/) | 50 × 10 |
| AirTAC | `SDA50X15` | [SDA-50-15-P-A](https://corneta.tech/pnevmocilindr-sda/sda-50-15-p-a/) | 50 × 15 |
| AirTAC | `SDA50X25` | [SDA-50-25-P-A](https://corneta.tech/pnevmocilindr-sda/sda-50-25-p-a/) | 50 × 25 |
| AirTAC | `SDA63X100` | [SDA-63-100-P-A](https://corneta.tech/pnevmocilindr-sda/sda-63-100-p-a/) | 63 × 100 |
| AirTAC | `SDA63X50` | [SDA-63-50-P-A](https://corneta.tech/pnevmocilindr-sda/sda-63-50-p-a/) | 63 × 50 |
| AirTAC | `SDA80X20` | [SDA-80-20-P-A](https://corneta.tech/pnevmocilindr-sda/sda-80-20-p-a/) | 80 × 20 |
| AirTAC | `SE40X700` | [DSBC-40-700-PPV-A](https://corneta.tech/pnevmocilindr-dsbc/dsbc-40-700-ppv-a/) | 40 × 700 |
| AirTAC | `SI100X100` | [SI-100-100-PPV-A](https://corneta.tech/pnevmocilindr-si/si-100-100-ppv-a/) | 100 × 100 |
| AirTAC | `SI100X500` | [SI-100-500-PPV-A](https://corneta.tech/pnevmocilindr-si/si-100-500-ppv-a/) | 100 × 500 |
| AirTAC | `SI125X800` | [SI-125-800-PPV-A](https://corneta.tech/pnevmocilindr-si/si-125-800-ppv-a/) | 125 × 800 |
| AirTAC | `SI63X200` | [SI-63-200-PPV-A](https://corneta.tech/pnevmocilindr-si/si-63-200-ppv-a/) | 63 × 200 |
| Camozzi | `16N2A12A015` | [DSNU-12-15-P-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-12-15-p-a/) | 12 × 15 |
| Camozzi | `16N2A12A030` | [DSNU-12-30-P-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-12-30-p-a/) | 12 × 30 |
| Camozzi | `23N2A25A010` | [DSNU-25-10-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-10-ppv-a/) | 25 × 10 |
| Camozzi | `23N2A25A015` | [DSNU-25-15-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-15-ppv-a/) | 25 × 15 |
| Camozzi | `23N2A25A020` | [DSNU-25-20-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-20-ppv-a/) | 25 × 20 |
| Camozzi | `23N2A25A030` | [DSNU-25-30-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-30-ppv-a/) | 25 × 30 |
| Camozzi | `23N2A25A040` | [DSNU-25-40-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-40-ppv-a/) | 25 × 40 |
| Camozzi | `23N2A25A060` | [DSNU-25-60-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-60-ppv-a/) | 25 × 60 |
| Camozzi | `23N2A25A075` | [DSNU-25-75-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-75-ppv-a/) | 25 × 75 |
| Camozzi | `23N2A25A150` | [DSNU-25-150-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-150-ppv-a/) | 25 × 150 |
| Camozzi | `23N2A25A175` | [DSNU-25-175-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-175-ppv-a/) | 25 × 175 |
| Camozzi | `23N2A25A200` | [DSNU-25-200-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-200-ppv-a/) | 25 × 200 |
| Camozzi | `23N2A25A250` | [DSNU-25-250-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-250-ppv-a/) | 25 × 250 |
| Camozzi | `23N2A25A300` | [DSNU-25-300-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-300-ppv-a/) | 25 × 300 |
| Camozzi | `23N2A25A400` | [DSNU-25-400-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-400-ppv-a/) | 25 × 400 |
| Camozzi | `23N2A25A500` | [DSNU-25-500-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-500-ppv-a/) | 25 × 500 |
| Camozzi | `40N2L100A0100` | [DSBG-100-100-PPV-A](https://corneta.tech/pnevmocilindr-dsbg/dsbg-100-100-ppv-a/) | 100 × 100 |
| Camozzi | `67MP2C080A0160` | [DSBG-80-160-PPV-A](https://corneta.tech/pnevmocilindr-dsbg/dsbg-80-160-ppv-a/) | 80 × 160 |
| Festo | `DSNU-16-25-PPS` | [DSNU-16-25-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-16-25-ppv-a/) | 16 × 25 |
| Festo | `DSNU-20-60-PPS` | [DSNU-20-60-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-20-60-ppv-a/) | 20 × 60 |
| Festo | `DSNU-25-10-PPS` | [DSNU-25-10-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-10-ppv-a/) | 25 × 10 |
| Festo | `DSNU-25-200-PPS` | [DSNU-25-200-PPV-A](https://corneta.tech/pnevmocilindr-dsnu/dsnu-25-200-ppv-a/) | 25 × 200 |
| SMC | `CXSM20-100` | [CXSM-20-100](https://corneta.tech/pnevmocilindr-cxsm/cxsm-20-100/) | 20 × 100 |
| SMC | `CXSM20-125` | [CXSM-20-125](https://corneta.tech/pnevmocilindr-cxsm/cxsm-20-125/) | 20 × 125 |
| SMC | `CXSM20-150` | [CXSM-20-150](https://corneta.tech/pnevmocilindr-cxsm/cxsm-20-150/) | 20 × 150 |
| SMC | `CXSM20-175` | [CXSM-20-175](https://corneta.tech/pnevmocilindr-cxsm/cxsm-20-175/) | 20 × 175 |
| SMC | `CXSM20-200-XB11` | [CXSM-20-200](https://corneta.tech/pnevmocilindr-cxsm/cxsm-20-200/) | 20 × 200 |
| SMC | `CXSM20-75` | [CXSM-20-75](https://corneta.tech/pnevmocilindr-cxsm/cxsm-20-75/) | 20 × 75 |
| SMC | `CXSM25-100` | [CXSM-25-100](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-100/) | 25 × 100 |
| SMC | `CXSM25-125` | [CXSM-25-125](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-125/) | 25 × 125 |
| SMC | `CXSM25-15` | [CXSM-25-15](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-15/) | 25 × 15 |
| SMC | `CXSM25-150` | [CXSM-25-150](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-150/) | 25 × 150 |
| SMC | `CXSM25-175` | [CXSM-25-175](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-175/) | 25 × 175 |
| SMC | `CXSM25-20` | [CXSM-25-20](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-20/) | 25 × 20 |
| SMC | `CXSM25-200-XB11` | [CXSM-25-200](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-200/) | 25 × 200 |
| SMC | `CXSM25-25` | [CXSM-25-25](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-25/) | 25 × 25 |
| SMC | `CXSM25-30` | [CXSM-25-30](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-30/) | 25 × 30 |
| SMC | `CXSM25-35` | [CXSM-25-35](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-35/) | 25 × 35 |
| SMC | `CXSM25-40` | [CXSM-25-40](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-40/) | 25 × 40 |
| SMC | `CXSM25-45` | [CXSM-25-45](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-45/) | 25 × 45 |
| SMC | `CXSM25-75` | [CXSM-25-75](https://corneta.tech/pnevmocilindr-cxsm/cxsm-25-75/) | 25 × 75 |

## Earlier exports and reference pages

The [historical per-brand CSV files](data/) were exported on 1 November 2026. They have a different schema and were **not revalidated under the checks above**. Their old `drop_in` and `near` labels should not be treated as current replacement certification. Use `checked/2026-11-16.csv` for the checked sample described here.

Existing reference pages: [GitHub Pages](https://ibr-alt.github.io/pneumatic-cross-reference/), [16 November](kody-2026-11-16.md), [8 November](kody-2026-11-08.md), [2 November](kody-2026-11-02.md).

## Attribution and corrections

Publisher and affiliation: **corneta.tech**, a supplier of industrial pneumatics. This is supplier-maintained data, independent of the named third-party manufacturers. Product and brand names identify their respective products and owners.

Reuse is permitted under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribute the data to “corneta.tech — pneumatic cross-reference data”, link this repository, and identify any changes. Report a suspected incorrect pair in this repository's issues with the brand, both codes and a catalog reference; corrections belong in the shared source before a new export.

## Кратко по-русски

Проверенный срез: **61 пара, 4 марки, 59 страниц типоразмеров**, дата 16.11.2026. Чужой код ведёт к кандидату WAALPC с указанными диаметром и ходом. Это не гарантия полной взаимозаменяемости. Источник один — ядро `wp_cv2_analog_index`; срез не заменяет его. Проверены точная пара в фактчеке, ядро, существующий SKU, оси и живой адрес. Старые файлы `data/` не проходили эту повторную проверку. Лицензия CC BY 4.0, издатель — corneta.tech.
