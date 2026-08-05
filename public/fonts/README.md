# Self-hosted fonts

These files are served from this origin. **Nothing on body-awareness.us may
reference `fonts.googleapis.com` or `fonts.gstatic.com`.** That is the whole
point of them being here: this site has no privacy policy, and it can only
defensibly have none if it makes no third-party request. A Google Fonts `<link>`
is a third-party request that hands Google the visitor's IP and User-Agent on
every page load.

The `@font-face` rules live in `src/styles/global.css`, immediately above the
`--font-body` / `--font-heading` tokens that name these families.

## Provenance

Both downloaded 2026-08-04 from the `latin` subset Google Fonts serves for:

    https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Playfair+Display:wght@500;600;700&display=swap

| File | Family | Axis | Source |
|---|---|---|---|
| `inter-variable.woff2` | Inter | `wght` 100–900 | `fonts.gstatic.com/s/inter/v20/UcC73FwrK3iLTeHuS_nVMrMxCp50SjIa1ZL7W0Q5nw.woff2` |
| `playfair-display-variable.woff2` | Playfair Display | `wght` 400–900 | `fonts.gstatic.com/s/playfairdisplay/v40/nuFiD-vYSZviVYUb_rj3ij__anPXDTzYgEM86xQ.woff2` |

Google serves **one** file per family for all the requested weights — both are
variable fonts — so the single `@font-face` per family with a `font-weight`
range is equivalent to the seven faces the `<link>` used to declare.

Licence: SIL Open Font License 1.1 for both.

## Subset

    pyftsubset <source>.woff2 \
      --output-file=<name>.woff2 --flavor=woff2 --layout-features='*' \
      --unicodes='U+0020-007E,U+00A0,U+00A9,U+00AE,U+00B0,U+00B7,U+00D7,U+00C0-00FF,U+0131,U+0152-0153,U+2013,U+2014,U+2018,U+2019,U+201C,U+201D,U+2022,U+2026,U+2039,U+203A,U+2044,U+2190,U+2192,U+20AC,U+2122,U+2212'

That alphabet is printable ASCII + the Latin-1 accented letters + Western
typographic punctuation. It is a **superset** of every character this site
actually renders (checked against `dist/**/*.html` on 2026-08-04), with the
accents kept deliberately so ordinary copy can be edited later without producing
a missing glyph.

Inter 48 432 → 34 924 bytes. Playfair Display 38 460 → 32 616 bytes.

The decorative characters this site uses — `⏰ ◈ ★ ☎ ⚛ ⚲ ✓ ✧ ✶ ✿ ❀ ❖` — are not
in the subset, and were not in Google's `latin` file either. They fell back to a
system font before this change and they fall back to the same system font after
it.

## If you add a font

Add it here, subset it, and reference it from a local `@font-face`. Do not add a
`<link>` to a font CDN.
