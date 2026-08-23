# Blasting Kidney Stones

An Asteroids-style arcade shooter set inside the urinary tract. You pilot a
lithotripsy probe, blasting kidney stones into gravel while dodging bacteria
colonies that shoot back.

Single file, no build step, no dependencies, no external assets — all graphics
are canvas vectors and all sound is synthesized with the Web Audio API.

## Play

Open `index.html` in any modern browser. That's it.

Or serve it locally if you prefer:

```sh
npx http-server blasting-kidney-stones
```

## Controls

| Input | Action |
| --- | --- |
| `←` `→` / `A` `D` | rotate probe |
| `↑` / `W` | thrust |
| `Space` | fire shock pulse |
| `Shift` | hyperspace jump |
| `P` / `Esc` | pause |
| `M` | mute |
| `Enter` | start / restart |

On phones and tablets an on-screen pad appears automatically.

## Rules

- Large stones split into two mediums, mediums into two smalls, smalls vaporize.
- Scoring: 20 (large), 50 (medium), 100 (small), 200 (large colony),
  1000 (small colony), plus a clearing bonus each stage.
- Clear every fragment to advance. Each stage adds a stone and speeds up the
  field, up to eleven.
- An extra probe every 10,000 points. Best score is kept in `localStorage`.
- Hyperspace teleports you anywhere on the field instantly, but there is an 8%
  chance you rematerialize inside a stone.
- Stones destroy bacteria on contact, so patience is sometimes a weapon.
- The heartbeat tempo tracks how much of the field you have left to clear.

## Layout

Everything lives in `index.html`: markup and CSS up top, then the game script —
canvas setup, synthesized audio, input, entities (probe, stones, bacteria,
particles), collision, rendering, and the main loop, in that order.

Not medical advice.
