# SlopTV open data: AI video benchmark scores and prices

Open dataset behind [SlopTV](https://sloptv.co), an independent benchmark and price tracker for AI video generation.
Every model runs the same 40 fixed prompts across 10 categories (hands, faces, liquids, text, lip-sync,
camera moves and more), every clip is scored, and published prices are tracked twice a day across 15 platforms and APIs.

- **13 models** benchmarked, **518 scored clips**
- **10,111 prices** for 14 models, last read 2026-10-08
- Updated automatically every day. The git history of `data/prices.csv` is a day-by-day record of AI video prices:
  each commit's diff shows exactly which prices moved. All prices in a commit were read on the date in its message.

Browse it on the site: [leaderboard](https://sloptv.co/leaderboard) · [price radar](https://sloptv.co/radar) · [methodology](https://sloptv.co/methodology) · [open data page](https://sloptv.co/data)

## Current leaderboard

| # | Model | Maker | Overall (0-5) | 95% CI |
|---:|---|---|---:|---:|
| 1 | [Google Gemini Omni](https://sloptv.co/model/gemini-omni) | Google | 4.91 | ±0.04 |
| 2 | [Kling 3.0 Turbo](https://sloptv.co/model/kling-3-0-turbo) | Kuaishou | 4.89 | ±0.07 |
| 3 | [FLUX 3](https://sloptv.co/model/flux-3) | Black Forest Labs | 4.83 | ±0.11 |
| 4 | [Seedance 2.0](https://sloptv.co/model/seedance-2-0) | ByteDance | 4.83 | ±0.16 |
| 5 | [Seedance 2.5](https://sloptv.co/model/seedance-2-5) | ByteDance | 4.82 | ±0.15 |
| 6 | [MiniMax H3](https://sloptv.co/model/hailuo-h3) | MiniMax | 4.81 | ±0.22 |
| 7 | [OpenAI Sora 2](https://sloptv.co/model/sora-2) | OpenAI | 4.78 | ±0.17 |
| 8 | [Grok Video](https://sloptv.co/model/grok-video) | xAI | 4.67 | ±0.19 |
| 9 | [Google Veo 3.1](https://sloptv.co/model/veo-3-1) | Google | 4.67 | ±0.25 |
| 10 | [Runway Gen-4.5](https://sloptv.co/model/runway-gen-4) | Runway | 4.63 | ±0.14 |
| 11 | [PixVerse v5.5](https://sloptv.co/model/pixverse-v5-5) | PixVerse | 4.58 | ±0.16 |
| 12 | [Kling 3.0](https://sloptv.co/model/kling-3-0) | Kuaishou | 4.45 | ±0.20 |
| 13 | [MiniMax Hailuo 02](https://sloptv.co/model/hailuo-02) | MiniMax | 3.93 | ±0.47 |

Full table with sub-scores and per-category scores: [`data/leaderboard.csv`](data/leaderboard.csv). Live version: [sloptv.co/leaderboard](https://sloptv.co/leaderboard).

## Files

| File | Rows | What it has |
|---|---:|---|
| [`data/leaderboard.csv`](data/leaderboard.csv) | 13 | One row per model: overall score, 95% confidence interval, sub-scores and the score in each test category. |
| [`data/scores.csv`](data/scores.csv) | 518 | One row per scored clip: model, prompt, category, round and every judge score, with a link to the clip. |
| [`data/prices.csv`](data/prices.csv) | 10,111 | Current published prices on every platform and API we track, normalised to USD per clip and per second. |

All files are UTF-8 CSV with a header row. [`datapackage.json`](datapackage.json) describes them in the [Frictionless Data](https://frictionlessdata.io/) format.

## Columns

### leaderboard.csv

| Column | Meaning |
|---|---|
| `rank` | Position by overall score (1 = best) |
| `model` | Model name |
| `slug` | Model id, also used in https://sloptv.co/model/{slug} |
| `company` | Maker |
| `overall` | Mean overall score across all clips, 0 to 5 |
| `ci95` | Half-width of the 95% confidence interval of overall |
| `fidelity` | Prompt fidelity, 0 to 5 |
| `visual` | Visual quality, 0 to 5 |
| `physics` | Physical plausibility, 0 to 5 |
| `consistency` | Temporal and identity consistency, 0 to 5 |
| `audio` | Audio quality and sync, 0 to 5 (empty when the model has no audio) |
| `attempts_until_usable` | Mean generations needed for a usable clip (empty when not recorded) |
| `runs` | Clips scored |
| `{category}` | Overall score within that test category (hands, faces, liquids, text_render, multishot, lipsync, camera, animals, style, img2video) |

### scores.csv

| Column | Meaning |
|---|---|
| `model` | Model name |
| `model_slug` | Model id |
| `prompt` | Prompt id, also used in https://sloptv.co/test/{prompt} |
| `category` | Test category |
| `round` | Benchmark round label |
| `score_overall` | Overall score, 0 to 5 |
| `score_fidelity` | Prompt fidelity |
| `score_visual` | Visual quality |
| `score_physics` | Physical plausibility |
| `score_consistency` | Consistency |
| `score_audio` | Audio |
| `attempts_until_usable` | Generations needed for a usable clip |
| `duration_s` | Clip length in seconds |
| `resolution` | Output resolution |
| `has_audio` | 1 if the clip has an audio track |
| `run_at` | Generation date (UTC) |
| `clip_page` | Page where the clip and its scores can be watched |

### prices.csv

| Column | Meaning |
|---|---|
| `model` | Model name |
| `model_slug` | Model id, also used in https://sloptv.co/radar/{model_slug} |
| `platform` | Platform or API selling it |
| `mode` | Model tier or speed mode as sold |
| `task` | Text-to-video, image-to-video, etc. (empty when the price is the same for all) |
| `resolution` | Output resolution |
| `audio` | 1 if the price includes generated audio |
| `duration_s` | Clip length the price refers to |
| `plan` | Subscription plan the credit price is computed on (empty for pay-as-you-go APIs) |
| `plan_usd_month` | Monthly price of that plan in USD |
| `usd_per_clip` | Cost of one clip of duration_s seconds, USD |
| `usd_per_second` | Same, per second of video |
| `is_entry_plan` | 1 for the cheapest plan that can run the model |
| `is_best_plan` | 1 for the plan with the lowest cost per clip |
| `exact` | 1 if read directly from the published price, 0 if derived (for example scaled to another clip length) |
| `promo` | 1 if it is a time-limited promotional price |

## How the data is made

**Scores.** Each clip is scored from 0 to 5 by a vision model that sees the original prompt but not which model made the clip,
on prompt fidelity, visual quality, physics, consistency and audio. Every score below 4 is checked by hand against frames
from the clip, and lip-sync lines are checked against the audio. The prompts are frozen: if one ever changes it becomes a new
round instead of rewriting old results. Details and known limits: [methodology](https://sloptv.co/methodology).

**Prices.** What each platform publishes for a US visitor, before tax, read twice a day (06:00 and 18:00 UTC). Credit and
subscription prices are converted to dollars assuming the plan's credits are spent on that model. Moves larger than 25% are
held for a manual check before they are published. Platforms tracked: Black Forest Labs API, BytePlus ModelArk, fal.ai, Google Gemini API, Higgsfield, Higgsfield API, Kling API, Luma API, Magnific, MiniMax API, OpenArt, Replicate, Runway, Runway API, xAI API.
How the radar works: [sloptv.co/radar](https://sloptv.co/radar).

Found an error? Open an issue or write to press@sloptv.co.

## License and attribution

[CC BY 4.0](LICENSE). Free to use, including commercially. The one condition is attribution with a link:

```html
Source: <a href="https://sloptv.co">SlopTV</a>
```

For papers, see [`CITATION.cff`](CITATION.cff) or use GitHub's "Cite this repository" button.
