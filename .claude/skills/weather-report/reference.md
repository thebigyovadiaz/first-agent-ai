# Weather report template

All text below — the code table, the markdown template, and the HTML
template — is written in **canonical English as a translation source**, not
as fixed output. Translate every description, heading, and label into the
report's detected language (see `SKILL.md` step 2) before writing either
output file.

## WMO weather code → description (canonical English)
| Code | Description |
|---|---|
| 0 | Clear sky |
| 1–3 | Partly cloudy |
| 45, 48 | Fog |
| 51–57 | Drizzle |
| 61–67 | Rain |
| 71–77 | Snow |
| 80–82 | Rain showers |
| 95–99 | Thunderstorm |

## Markdown output template (`<base>.md`)

# Weather report — <City>, <Country>

Generated: <ISO timestamp>

## Current conditions
- Temperature: <temp>°C
- Conditions: <weather description>
- Humidity: <humidity>%
- Wind: <wind speed> km/h

## 3-day forecast
| Date | Condition | High | Low |
|---|---|---|---|
| ... | ... | ...°C | ...°C |

## HTML output template (`<base>.html`)

Fill in every `<placeholder>` with the same values used in the markdown
report, translated into the detected language — the labels below (`Weather
report`, `Generated`, `Current conditions`, `Temperature`, `Conditions`,
`Humidity`, `Wind`, `3-day forecast`, `Date`, `Condition`, `High`, `Low`) are
English canonical text, not fixed output. Set `lang` to the matching BCP 47
code (`es`, `en`, …). Repeat the `<tr>` inside `<tbody>` once per forecast
day. This file must be fully self-contained — no external stylesheets,
fonts, or scripts.

```html
<!doctype html>
<html lang="<language-code>">
<head>
<meta charset="utf-8">
<title>Weather report — <City></title>
<style>
  :root {
    --bg: #f4f6f8;
    --card: #ffffff;
    --ink: #1a2330;
    --ink-soft: #5b6675;
    --border: #dde3ea;
    --accent: #2563eb;
  }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    padding: 2.5rem 1.5rem;
    background: var(--bg);
    color: var(--ink);
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  }
  .card {
    max-width: 560px;
    margin: 0 auto;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.75rem 2rem;
    box-shadow: 0 1px 2px rgba(0,0,0,.04), 0 8px 20px rgba(0,0,0,.05);
  }
  h1 { font-size: 1.4rem; margin: 0 0 .25rem; }
  .generated { color: var(--ink-soft); font-size: .85rem; margin: 0 0 1.5rem; }
  h2 { font-size: 1rem; text-transform: uppercase; letter-spacing: .04em;
       color: var(--ink-soft); margin: 1.5rem 0 .75rem; }
  .current { display: grid; grid-template-columns: 1fr 1fr; gap: .6rem 1rem; }
  .current div { font-size: .95rem; }
  .current strong { display: block; font-size: 1.6rem; color: var(--accent); }
  table { width: 100%; border-collapse: collapse; font-size: .9rem; }
  th, td { text-align: left; padding: .5rem .4rem; border-bottom: 1px solid var(--border); }
  th { color: var(--ink-soft); font-weight: 600; }
</style>
</head>
<body>
  <div class="card">
    <h1>Weather report — <City>, <Country></h1>
    <p class="generated">Generated: <ISO timestamp></p>

    <h2>Current conditions</h2>
    <div class="current">
      <div><strong><temp>°C</strong>Temperature</div>
      <div><strong><weather description></strong>Conditions</div>
      <div><strong><humidity>%</strong>Humidity</div>
      <div><strong><wind speed> km/h</strong>Wind</div>
    </div>

    <h2>3-day forecast</h2>
    <table>
      <thead><tr><th>Date</th><th>Condition</th><th>High</th><th>Low</th></tr></thead>
      <tbody>
        <tr><td><date></td><td><condition></td><td><high>°C</td><td><low>°C</td></tr>
      </tbody>
    </table>
  </div>
</body>
</html>
```
