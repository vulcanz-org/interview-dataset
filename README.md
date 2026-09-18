# Interview Dataset — Preplan Normalization

Sample data for a coding-interview exercise. It models fire-department
**pre-incident plans** ("preplans") — the building records a fire department keeps
for the structures in its response area: address, occupancy and construction type,
sprinkler/standpipe protection, hydrants, hazardous materials, utility shutoffs and
site contacts.

Ten fictional departments each publish the same kind of record in a **different file
format and a different schema**, which is the point of the exercise.

## ⚠️ All of this data is fake

**Every department, facility, address, coordinate, phone number and person in this
repository is invented.** Nothing here is derived from, or based on, any real fire
department, any real building, or any customer, production or otherwise non-public
data. It was produced by a generator script that writes out hand-authored fictional
records.

Several details are deliberately chosen so no record can be mistaken for a real one:

| Field | Convention used here |
| --- | --- |
| State | `ZZ` — not a USPS state code; the departments sit in a fictional state |
| ZIP codes | `000xx` / `001xx` — ranges the USPS does not assign |
| Phone numbers | Area code `555` with `555-xxxx` exchanges — the reserved-for-fiction range |
| Coordinates | ~`37°N 142°W`, open Pacific Ocean — no real municipality is there |
| Facility names | Invented; any resemblance to a real hospital, school or plant is coincidental |

The realistic-*looking* messiness (inconsistent units, null spellings, date formats,
and so on) is intentional — it is what candidates are asked to work through — but the
underlying values are fabricated.

## Contents

| File | Department | Format | Notable characteristics |
| --- | --- | --- | --- |
| `data/dept01_argent_city.json` | Argent City FD | Nested JSON | Comparatively clean; ISO dates |
| `data/dept02_brackwater.csv` | Brackwater FPD | Flat CSV | Multi-value cells with `;`/`\|` subdelimiters; single-line addresses; `Y`/`N`; coordinates in `lon,lat` order; `MM/DD/YYYY` |
| `data/dept03_thornmere.xml` | Thornmere FD | XML | Nested elements; local occupancy vocabulary |
| `data/dept04_coldpine_county.yaml` | Coldpine County FD | YAML | Hand-maintained; free-text occupancy; `lat, lon` packed into one string |
| `data/dept05_merrowlake.tsv` | Merrowlake FD | TSV | `1`/`0` booleans; `-` for null; NFPA letter occupancy codes |
| `data/dept06_westmarch.json` | Westmarch FD | JSON | **Metric units** (m², L/min, mm, kPa) and different field names |
| `data/dept07_ironcrest.txt` | Ironcrest FD | Pipe-delimited text | Header comment block declares the layout; `NULL` sentinel; DMS coordinates |
| `data/dept08_ashvale.dat` + `.fmt` | Ashvale FD | Fixed-width | Column spec lives in the sibling `.fmt`; Julian (`YYYYDDD`) dates |
| `data/dept09_tidewell.xml` | Tidewell FD | XML | Different tag names again; `Y`/`N`; DMS coordinates; address on one line |
| `data/dept10_crestvale.jsonl` | Crestvale FD | JSON Lines | Numbers stored as strings; mixed date formats across records |

Across the set you will find the usual real-world drift: imperial vs. metric units,
several coordinate encodings, competing occupancy vocabularies, five ways of
saying "null" (`""`, `-`, `N/A`, `NULL`, `unknown`, plus keys that are simply absent),
four boolean encodings, inconsistent phone and date formats —
and, because neighbouring departments run mutual aid, a few facilities that appear in
more than one export with **conflicting** values.

## Regenerating

The data files are generated and checked in, so the repository is usable without
running anything. The generator itself is intentionally not published: it carries the
canonical values the exercise expects candidates to reconstruct.

## Questions

Open an issue, or contact the repository owner.
