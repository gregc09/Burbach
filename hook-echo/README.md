# Hook Echo

A top-down storm chase. You are Natalie, driving chase unit 7 north across a
plains town while the tornado takes it apart around you. Five nights, five
ratings, EF1 through EF5. Reach the shelter before the inflow gets under the
truck and the ground lets go.

Named for the radar signature that means one is on the ground.

Single file, no build step, no dependencies, no external assets except the two
webfonts. All graphics are canvas, all sound is synthesized with the Web Audio
API.

## Play

Open `index.html` in any modern browser. That's it.

```sh
npx http-server hook-echo
```

## Controls

| Input | Action |
| --- | --- |
| `←` `→` / `A` `D` | steer |
| `↑` / `W` | throttle |
| `↓` / `S` | brake, then reverse |
| `Space` | deploy a sensor probe |
| `P` / `Esc` | pause |
| `M` | mute |
| `Enter` | start / continue |

On phones and tablets a steering pad appears automatically. The throttle is
held down for you there — tap `GAS` to coast.

## The five nights

1. **EF1 — The Rope.** One thin funnel that wanders more than it tracks. This
   is where you learn what the inflow feels like through the wheel.
2. **EF2 — The Stovepipe.** Two on the ground, both crossing the highway ahead
   of you. The second one is hidden in the rain until it isn't.
3. **EF3 — The Drill.** Three turning through the middle of town, taking roofs
   off as they go, and hail.
4. **EF4 — The Grinder.** Four, one of them a half-mile wide, and the grid is
   down. What you can see is what the lightning gives you.
5. **EF5 — The Wedge.** One slow monster with satellite vortices spinning off
   its flank. Nothing about it is survivable at a standstill.

## Rules

- **Lift is the thing that kills you.** Every funnel carries a wind field: a
  tangential component that wants to spin you around it and a radial one that
  wants to bring you in. Sit in that field and the lift meter climbs. At 100 the
  ground lets go and the run is over.
- Lift accrues by *dwell*, and a stationary truck is a sail — standing still in
  the inflow costs you nearly twice what driving through it does. Speed is
  safety. Getting inside the core is fatal in about a second.
- **Grip is why the road matters.** On pavement the tyres kill sideways motion.
  On grass they mostly don't, which is how the wind takes you.
- Sheet metal, fence boards, tyres, downed lines and the occasional cow are all
  thrown by the funnel and all cost bodywork. A hundred points of damage and the
  truck will not roll. One impact is one impact — a scrape can't grind you down
  frame by frame.
- **Probes are the risk-for-score loop.** A probe is worth what it can see, and
  what it can see depends on how close to the funnel you were willing to get:
  150 points at the edge of the field, up to 2,500 right against the core. If
  the funnel later walks over a probe you left behind, that's a direct sample
  and another 3,000.
- People are waiting outside houses in the lit doorways. Slow down next to one
  and they board; deliver them to the shelter for 900 each. Get pulled up and
  they go with you.
- Three units, one more every 25,000 points. Best score is kept in
  `localStorage`.

## Layout

Everything lives in `index.html`: markup and CSS first, then the game script —
canvas, utils, audio, input, level data, storage, state, town generation, truck,
tornadoes, debris, probes, survivors, weather, radio, camera, collision, HUD,
radar, drawing, level flow, and the main loop, in that order.

Levels are data. Each entry in `LEVELS` sets the funnel count, core size, reach,
pull, lift rate, track speed, debris rate, rain, hail, darkness, probe count and
how many people are out there. The EF ladder is that table and nothing else.

The town is a plains grid: north-south roads every 320px, east-west every 360px,
with a farmstead, a main-street block, a pair of houses or an empty field in
each block. The funnels chew through it as they pass, and the rubble they throw
is the same debris that can end your run.

More Twister than Wizard of Oz. No ruby slippers, no flying bicycles.
