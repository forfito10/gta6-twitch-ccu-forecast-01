# gta6-twitch-ccu-forecast-01

[![make.fun · gta6-twitch-ccu-forecast-01](https://make.fun/badge/gta6-twitch-ccu-forecast-01.svg)](https://make.fun/bounty/gta6-twitch-ccu-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01)
[![rank](https://make.fun/badge/gta6-twitch-ccu-forecast-01/forfito10/gta6-twitch-ccu-forecast-01/rank.svg)](https://make.fun/bounty/gta6-twitch-ccu-forecast-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01)
[![reward](https://make.fun/badge/gta6-twitch-ccu-forecast-01/forfito10/gta6-twitch-ccu-forecast-01/reward.svg)](https://make.fun/bounty/gta6-twitch-ccu-forecast-01?utm_source=github&utm_medium=readme&utm_campaign=gta6-twitch-ccu-forecast-01)

Hour-by-hour quantile forecast of the "Grand Theft Auto VI" Twitch category's
concurrent viewers for release day 2026-11-19 (UTC), entered in
[make.fun's forecast competition](https://make.fun/bounty/gta6-twitch-ccu-forecast-01).

## What it does

`main.py` (Python 3.13, standard library only) reads one case file
`/input/<id>.in` — the category's history up to the end of the release day's
first hour plus that hour's print — and writes `/output/<id>.out` with five
quantiles (0.05, 0.25, 0.5, 0.75, 0.95) for each of hours 2..24.

The model treats the release day's shape as a repeatable pattern across past
midnight-unlock console launches: for each comparable launch in the case's
`comparables` it computes the ratio of each later hour's viewers to hour 1's,
takes the cross-launch median path as the median forecast and sizes the
quantile spread from the comparables' log dispersion (a guardrail floor and
ceiling bound it).

## Running locally

```
mkdir -p out && MAKEFUN_INPUT_DIR=<kit>/input MAKEFUN_OUTPUT_DIR=out python3 main.py
```

Deterministic; two runs on the same case produce byte-identical output.

## License

MIT (see `LICENSE`).
