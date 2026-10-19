# Life Clock

A clock that measures time at seven scales at once, from the passing second to a whole human life. One HTML file, no dependencies.

## Why I made it

I wanted a clock that also showed my week passing by. An ordinary clock tells you where you are in the day, but nothing tells you where you are in the week, and the week is the unit I actually live in. So I drew a ring for it, with the hand ending inside its own circle and the ring filling in as the week ran down.

It looked good, so I added the month. Then, inspired by Wait But Why's [Your Life in Weeks](https://waitbutwhy.com/2014/05/life-weeks.html), I added my entire life to the clock — one ring, from my birth year to a reasonable guess at the end.

I don't find it morbid (mostly). I find it refocuses me on not wasting precious time. The seconds ring moves fast enough to feel urgent and the life ring moves so slowly you can't see it move at all, and having both on the same dial is the entire point. Enjoy it, use it, share it.

## The rings

From the centre outward, each ring fills in as its cycle completes and carries its own hand, drawn as a distinct arrowhead running from the hub out to its own ring.

| Ring | Measures | Marked |
|---|---|---|
| Life | birth year to birth year + lifespan | a tick per year, labelled each decade |
| Year | January 1 to December 31 | the twelve months |
| Month | the 1st to the 28th, 29th, 30th or 31st | every day of this month |
| Week | Monday to Sunday | the seven days |
| Day | midnight to midnight | all 24 hours |
| Hour | the minutes of this hour | every 5 minutes |
| Minute | the seconds of this minute | every 5 seconds |

Every hand sweeps continuously from exact fractional time rather than ticking, so the second hand glides and the life hand creeps imperceptibly.

## Using it

Open `index.html` in a browser. That's all — it's one file with no dependencies, no build step and no network requests.

- **Set your start year and lifespan** in the two fields at the centre. Defaults are 1990 and 85 years. It remembers both, along with your theme and which rings you have showing, so it comes back the way you left it.
- **Turn rings on and off** with the checkboxes in the corner key. The remaining rings spread out to fill the dial.
- **Switch themes** with the auto / light / dark button. Auto follows your system setting.

If you'd rather serve it than open the file directly:

```
python3 -m http.server 8000
```

then visit http://localhost:8000.

## Watching the slow rings move

The outer rings are satisfying immediately; the inner ones are not. Two query parameters help:

- `?rate=20000` runs time fast, so the day, week and month rings visibly turn.
- `?t=2026-12-31T23:59:50` starts the clock at a given instant, which is the easy way to watch a year roll over.

They combine: `?t=2026-02-28T12:00:00&rate=5000`.

## Notes

Dates come from the browser's local calendar, so leap years, months of 28 to 31 days, and 23- and 25-hour daylight-saving days all come out right rather than being approximated at 365.25 days or a flat 24 hours.

Your settings are kept in `localStorage` under a single key, `lifeclock.v1`. Nothing is sent anywhere — there is no server, no analytics and no network traffic of any kind.
