---
name: weather-report
description: Formats raw weather data (current conditions + forecast, e.g. from Open-Meteo) into a markdown report and a standalone HTML report, in the same language the report was requested in, saves both to reports/, and summarizes in chat. Use when asked to write, format, or save a weather report from data that's already been fetched.
---

# Weather report formatter

1. Expect raw weather data as input: a location name/country, current
   conditions (temperature, humidity, wind, weather code), and a multi-day
   forecast (date, weather code, high/low temps).
2. Detect the report's language from how it was requested (the user's own
   words in this conversation). If it's ambiguous or mixed, default to
   Spanish.
3. Translate any WMO weather codes using the table in `reference.md` (given
   in English) into the detected language before writing the report — never
   show a raw numeric code, and never leave a description in a different
   language than the rest of the report.
4. Translate every heading and label in both templates in `reference.md`
   into the detected language too — they're written in English there as the
   canonical version to translate from, not as fixed output text. Set the
   HTML template's `lang` attribute to the matching BCP 47 code (e.g. `es`,
   `en`).
5. Build a filename base from the location and the current local date and
   time (24-hour clock): `weather-<location-slug>-<YYYY-MM-DD>-<HHmm>`
   (e.g. `weather-santiago-2026-09-07-1432`). Using time, not just date,
   means running the report twice in a day never overwrites the first run.
6. Save TWO files to `reports/` (create it if it doesn't exist), one per
   template in `reference.md`, both in the detected language:
   - `<base>.md` — the markdown report
   - `<base>.html` — a standalone, self-contained HTML report (inline CSS,
     no external requests) with the same content
7. Print the same summary in the chat reply too, in the same language —
   current conditions and the 3-day forecast — so the reader doesn't have to
   open either file for the headline numbers.
8. If a required value is missing (e.g. no forecast data), say so rather than
   inventing a plausible-looking number.
