# futbolik — public feed

Public data feed and legal pages for the **futbolik** Android app, published by
**Ayns Logic**.

This repository contains no application source code. It exists so the app can
fetch its data from a static, free, CDN-backed location, and so the privacy
policy has a permanent public URL (a Google Play requirement).

## Contents

| Path | What it is |
|---|---|
| `data/version.json` | Small manifest the app checks on every launch. |
| `data/data.json` | Full payload: fixtures for the next 4 days with computed statistics. |
| `privacy.html` | Privacy policy (Play store requirement). |
| `terms.html` | Terms of use. |

## `version.json`

```json
{
  "schema": 1,
  "build": "20260817202608",
  "generated_at": "2026-08-17T20:26:08.000Z",
  "min_app_version": "1.0.0",
  "match_count": 85,
  "league_count": 26
}
```

The app downloads this on every launch (a few hundred bytes) and only fetches
`data.json` when `build` has changed.

`min_app_version` is the lowest app version allowed to run. Raising it shows a
full-screen update wall in older installs — it is bumped deliberately, never
automatically.

## `data.json`

Regenerated once a day by an automated job. Roughly 420 KB, about 105 KB over
the wire once compressed.

**All timestamps are ISO 8601 UTC** (`2026-08-17T20:00:00.000Z`). Times are
never pre-formatted — the app renders them in the device's own time zone. A
match disappears from the list 105 minutes after kickoff, which the app decides
from the device clock.

Fields are only ever added, never removed or renamed, so older app versions keep
reading newer files.

## Contact

<aynslogic@gmail.com>
