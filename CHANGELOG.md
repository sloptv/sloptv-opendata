# Changelog

What changed in the data, day by day: price moves, new offers, new cheapest platforms, leaderboard changes and new benchmark clips. Prices are per second of video on each platform's best plan; the full detail of every change is in the commit diff.

**Last checked: 2026-10-09.** Prices are re-read twice a day; a day with no entry below is a day with no changes (nothing has moved since 2026-10-06).

By month: [2026-10](changelog/2026-10.md)

## 2026-10-06

### Dataset

- First public release of this dataset on GitHub: 13 models, 518 scored clips and 10,111 prices from 15 platforms and APIs.

## 2026-10-04

### Leaderboard

- **New model: FLUX 3** enters at #3 with 4.83/5, level with Seedance 2.0, after 40 scored clips. It has perfect scores on on-screen text, lip-sync and multi-shot tests. [Clips and scores](https://sloptv.co/model/flux-3)

### Prices

**New offers:**
- FLUX 3 on Black Forest Labs API, the model's official API, and on fal.ai ([radar](https://sloptv.co/radar/flux-3))

## 2026-10-03

### Prices

**New sources:** the radar now also reads the model makers' own APIs, so resellers can be compared with the official price.
- Google Gemini API, Kling API, MiniMax API, Luma API, xAI API and BytePlus ModelArk (ByteDance)
- Magnific and OpenArt

## 2026-10-02

### Prices

19 price changes (13 down, 6 up). Best plan, per second of video; when a change covers several variants, the cheapest one is shown:

| Model | Platform | Variant | Before | Now | Change |
|---|---|---|---:|---:|---:|
| [MiniMax H3](https://sloptv.co/radar/hailuo-h3) | Higgsfield API | 3 variants (2k) | $0.091/s | $0.065/s | -28.6% |
| [MiniMax H3](https://sloptv.co/radar/hailuo-h3) | fal.ai | 6 variants of H3 Max (480p, 768p and 1080p) | $0.025/s | $0.03/s | +20.0% |
| [Kling 3.0](https://sloptv.co/radar/kling-3-0) | Higgsfield API | 9 variants | $0.0462/s | $0.042/s | -9.1% |
| [Kling 3.0 Turbo](https://sloptv.co/radar/kling-3-0-turbo) | Higgsfield API | 4 variants (720p and 1080p) | $0.0616/s | $0.056/s | -9.1% |

Higgsfield's API listed these models without their discounts for one day on 1 October, then settled at the lower prices above.

**No longer listed:**
- Luma Ray 2 and Ray 2 Flash on fal.ai: 4 variants (fal marks both as deprecated)
