# DOT CLOCK

An offline dot-matrix clock by **ABE** for CORSAIR XENEON EDGE. The design is inspired by Nothing OS; this independent widget is not affiliated with or endorsed by Nothing, CORSAIR, or Elgato.

Marketplace listing preparation: **US$8.99**. Support: **abdullam.09@gmail.com**. See `marketplace/LISTING.md` for listing copy and `marketplace/SUBMISSION.md` for the submission handoff.

## Install

Import the included `.icuewidget` file using iCUE's widget import function, then add DOT CLOCK to your XENEON EDGE layout. Requires Windows and iCUE 5.47 or later as declared in the manifest. No plugins, accounts, API keys, fonts, or network service are required.

Open the widget's iCUE settings to customize it. Enable **Custom Style** in the personalization tab to use the supplied off-white, red, and black palette or your own colors; when Custom Style is disabled, iCUE may supply the device theme colors. Changes apply immediately.

## Settings

| Setting | Default / behavior |
| --- | --- |
| Time Format | 24 hour; optional 12 hour with AM/PM |
| Show Seconds | On; small accent-colored dot digits |
| Blink Colon | Off; optional once-per-second change, suppressed by reduced-motion preference |
| Show Date | On |
| Date Format | Weekday and date; short locale date or year-month-day also available |
| Time Zone | `local`; enter an IANA name such as `America/New_York`, `Europe/London`, `Asia/Tokyo`, or `UTC` |
| Dot Shape | Round; square also available |
| Dot Spacing | 24%; range 10–48% |
| Show Inactive Dots | Off; optional subtle matrix guide |
| Text Color | `#f2f0e9` |
| Accent Color | `#ed403b` |
| Background Color | `#080808` |
| Background Image | None; local PNG, JPG, JPEG, or WebP with iCUE positioning controls |
| Background Brightness | 40%; applies to image only |
| Glass Blur | 0; range 0–30 |
| Background Transparency | 0%; 100% makes the outer background transparent; solid backing behind the clock and labels preserves legibility |

Low-contrast text and accent choices automatically resolve to readable black or white. Background images remain outside the solid content backing. This protects readability across custom colors, media, and transparent host backgrounds.

The clock reads the computer clock every second and rechecks on visibility changes. Named zones use the browser's time-zone database, including daylight-saving rules. Dates follow the iCUE interface language, or browser language in standalone preview. Settings labels are currently English.

## Layouts

Browser-verified slots: 840×344, 696×416, 840×696, 696×840, 1688×696, 696×1688, 2536×696, and 696×2536. Wide slots use a single time row; tall slots stack hours over minutes. Portrait typography stays the same size as the slot grows taller. Only `dashboard_lcd` is declared; other devices are not supported.

## Recovery and privacy

The clock renders immediately without a network loading state. Offline use requires no special handling. An invalid time zone shows a small warning and falls back to local time. An unreadable clock shows dash digits and a computer-clock hint. A missing background image falls back to the selected solid color. No telemetry or outbound requests are used.

## Project files and editing

- `widget/` — complete importable widget source, including manifest, icon, and translations.
- `src/clock.css` and `src/clock.js` — editable style and runtime.
- `src/media-viewer.html` — ABE local-image renderer using the documented media-selector transform fields.
- `build.py` — Python standard-library build; generates inline CSS/JS to avoid local-file script loading issues.
- `settings.json` — generated settings reference; controls are authored in `build.py`.
- `preview-*.png` — verified sample screenshots, set to a fixed sample time in UTC.
- `verification.json` — browser verification summary.

From this project directory:

```powershell
python build.py
icuewidget validate widget
icuewidget package widget
```

Open `widget/index.html` in a browser for a live default clock preview. Customize through iCUE after import.

## Validation status

Validated with Widget Builder CLI 0.4.47 and tested in headless Microsoft Edge at all eight slots. Browser checks simulate iCUE global properties and callbacks and cover midnight, date rollover, time zones, settings, media transforms, reduced motion, contrast, and expanded translations. No browser script errors or outgoing HTTP requests were observed. Physical XENEON EDGE and actual iCUE import/rendering have not been tested. Marketplace submission materials are included; the product has not been submitted, reviewed, or published.

The Marketplace identity is `com.abe.dotclock`, version `1.0.0`. The earlier private prototype used `com.personal.dotclock`; importing the ABE version creates a separate widget. Existing private settings will not migrate automatically. Keep the ABE identifier stable for future published updates.
