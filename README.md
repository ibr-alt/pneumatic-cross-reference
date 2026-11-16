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

## Earlier exports and reference pages

The [historical per-brand CSV files](data/) were exported on 1 November 2026. They have a different schema and were **not revalidated under the checks above**. Their old `drop_in` and `near` labels should not be treated as current replacement certification. Use `checked/2026-11-16.csv` for the checked sample described here.

Existing reference pages: [GitHub Pages](https://ibr-alt.github.io/pneumatic-cross-reference/), [16 November](kody-2026-11-16.md), [8 November](kody-2026-11-08.md), [2 November](kody-2026-11-02.md).

## Attribution and corrections

Publisher and affiliation: **corneta.tech**, a supplier of industrial pneumatics. This is supplier-maintained data, independent of the named third-party manufacturers. Product and brand names identify their respective products and owners.

Reuse is permitted under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribute the data to “corneta.tech — pneumatic cross-reference data”, link this repository, and identify any changes. Report a suspected incorrect pair in this repository's issues with the brand, both codes and a catalog reference; corrections belong in the shared source before a new export.

## Кратко по-русски

Проверенный срез: **61 пара, 4 марки, 59 страниц типоразмеров**, дата 16.11.2026. Чужой код ведёт к кандидату WAALPC с указанными диаметром и ходом. Это не гарантия полной взаимозаменяемости. Источник один — ядро `wp_cv2_analog_index`; срез не заменяет его. Проверены точная пара в фактчеке, ядро, существующий SKU, оси и живой адрес. Старые файлы `data/` не проходили эту повторную проверку. Лицензия CC BY 4.0, издатель — corneta.tech.
