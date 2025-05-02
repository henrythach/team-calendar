# Team Calendar Viewer

A lightweight, shareable web calendar that displays team scrum meetings and company holidays based on URL query parameters. Useful for embedding, linking, or sharing fixed yearly views without needing a backend or authentication.

## 🗓 Features

- View sprint events: Planning, Refinement, Retrospective, Sprint Review.
- Label and highlight company holidays.
- Data is encoded entirely in the URL (no backend required).
- One-year view for simple planning and visibility.
- Can support multiple events per day.
- Light mode and dark mode supported.

## 🔗 URL Parameters

### `events`

Represents team ceremonies. Accepts a comma-separated list of `YYYYMMDD:TYPE` pairs.

#### Event type codes:

- `SP` – Sprint Planning (🧠)
- `RF` – Refinement (🛠)
- `RT` – Retrospective (🔁)
- `SR` – Sprint Review (📊)
- `TH` - Team Hangout (🙌)

> [!NOTE]
> Daily Standup is intentionally not supported as a calendar event. Since it occurs every working day by default, displaying it would add unnecessary clutter. This calendar focuses on events that are less frequent and more variable in scheduling, such as planning, reviews, and holidays.

#### Example:

```
?events=20250108:SP,20250110:RF,20250117:RT,20250122:SR
```

> [!WARNING]
> If an invalid event type is specified, the ⭐️ emoji will be displayed with "Unknown" as the label.

### `holidays`

Represents company holidays with labels. Accepts a comma-separated list of `YYYYMMDD:Label` pairs.

#### Example:

```
?holidays=20251127:Thanksgiving,20251225:Christmas
```

> [!NOTE]
> Labels with spaces should be URL-encoded (e.g., `New%20Year`).

### `year`

Represents which year to render. (Defaults to the current year.)

#### Example:

```
?year=2026
```

## 🧠 How It Works

The app:

1. Parses `events` and `holidays` from the current URL.
2. Maps dates using `Date.getTime()` for efficient keying.
3. Displays a calendar with events and holiday names annotated.

## 📦 Getting Started

No installation required. Just open `index.html` in a browser or deploy to static hosting (e.g. GitHub Pages, Netlify).

To test locally:

```bash
open index.html
```

Then try adding query parameters in the browser:

``` 
file:///path/to/index.html?events=20250108:SP&holidays=20251225:Christmas
```

## 🚧 Roadmap Ideas

- Add custom events (e.g., `?legend=XX:🌸:Custom+Label`)
- Support event description override (e.g., `?events=20250501:RT:Action+Item+Follow+Up`)
- Add support for recurring events (e.g., `20250108/14:SP`).
- Add support for date ranges for holidays (e.g., `20251225..20260101:Holiday%20Break`).
