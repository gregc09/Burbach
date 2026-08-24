# Bait Station

A Donkey Kong-style single-screen climber played from three inches off the
floor. You are a house mouse. The house has been treated. Climb it anyway —
the last of the litter is at the top of each floor.

The mouse wears a real face: a photograph cropped to a circle, reduced to a
40-pixel sprite and drawn on a pixel-art body, the way arcade cabinets
digitised actors in the early nineties. It is embedded in the page as a data
URI, so the game is still one file with nothing to fetch. Swap it by replacing
the base64 string assigned to `FACE.src`; anything roughly square and centred
on a face works, and the sprite is drawn at 16 logical pixels, so crop tight.

Single file, no build step, no dependencies, no external assets except the two
webfonts. Everything else is canvas pixel art, and all sound is synthesized
with the Web Audio API.

## Play

Open `index.html` in any modern browser. That's it.

```sh
npx http-server bait-station
```

## Controls

| Input | Action |
| --- | --- |
| `←` `→` / `A` `D` | scurry |
| `↑` `↓` / `W` `S` | cords, conduit and ladders |
| `Space` / `Z` | hop |
| `P` / `Esc` | pause |
| `M` | mute |
| `Enter` | start / restart |

On phones and tablets a d-pad and a HOP button appear automatically.

## The four floors

1. **The Kitchen** — six sloped shelves. A bait box at the top drips turquoise
   wax blocks that roll down the slopes and sometimes take a ladder instead of
   the drop. They dissolve in the tray at the bottom left, and every third one
   or so leaves a vapour wisp behind that hunts you. Reach the nest.
2. **The Utility Room** — two lift shafts running on a loop, wall nozzles that
   fog across the shafts, and a snap trap hopping along the top ledge. Ride up
   the right shaft, cross the top, drop into the left shaft, reach the nest.
3. **The Cellar** — eight bait blocks wedged at the inner end of every
   half-floor. Chew all eight. Each one you take shortens the walkway you are
   standing on, and four wisps are loose in the room.
4. **The Foreman** — three technicians patrol the tiers, each spraying a
   drifting cloud. Above them the Foreman stands on his rig with a fogger tank
   fed by six valves. Chew all six. Every valve you take makes him faster,
   angrier, and quicker to stomp blocks loose from the ceiling.

## Rules

- Contact with poison, vapour, spray, a snap trap, a technician or the Foreman
  costs a mouse. Three mice, one extra every 20,000 points.
- Hopping a rolling block scores 100. Crumbs are 300, bait blocks 400,
  valves 800.
- A wad of steel wool makes you dangerous for eight seconds: anything poisonous
  you touch is destroyed for 500. You cannot climb with it in your mouth.
- The bonus timer drains the whole time and is paid out when the floor is
  cleared. Let it hit zero and you lose a mouse.
- Blocks and valves you have already chewed stay chewed when you lose a mouse.
- Broken ladders end in a splintered stub. They go nowhere, but a pellet will
  never come down one.
- Best score is kept in `localStorage`.

## Layout

Everything lives in `index.html`: markup and CSS first, then the game script —
display scaling, synthesized audio, input, level tables, platform/ladder
physics, entities (mouse, pellets, wisps, clouds, snap traps, lifts,
technicians, Foreman), collision, drawing, and the main loop, in that order.

Levels are data. A floor is a list of sloped platform segments, a list of
ladders naming the two segments they join, and a handful of spawn tables;
`buildLevel` resolves names to segments and computes every ladder's top and
bottom from the slope it lands on.

No rats, no restaurants, no cooking.
