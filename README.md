# WARD 13 — a StarfallEx horror room

A single StarfallEx chip that builds a ten-room, walk-through horror house and runs it:
doors that seal behind you, flickering lamps with real shadows, things that only move
when nobody is looking, and a last room you have to run through.

## Install

1. Copy [`horror_room.txt`](horror_room.txt) into `garrysmod/data/starfall/`.
2. In game, open the Starfall editor, load `horror_room.txt` and place the chip with the
   Starfall processor tool.

Needs [StarfallEx](https://github.com/thegrb93/StarfallEx) only. Every model, sound and
material is stock Garry's Mod / Half-Life 2 content.

## Placing it

- Stand on **flat, open ground** with about **2000 × 800 units** free in front of you
  (`gm_flatgrass` is ideal) and place the chip at your feet.
- The ward is built *away from you*, starting a little past the chip. Building takes
  roughly 12 seconds (props are rate limited); the chip tells you in chat when it is ready.
- Enter through the **left** door. The exit is the right door, ten rooms later.

Budget: about 46 props and 161 holograms (of StarfallEx's default 200). If your hologram
budget is short the cast is created first and decoration is skipped; if the prop limit
is hit the chip says so instead of half-building.

## The ten rooms

| # | Room | What happens | How it ends |
|---|------|--------------|-------------|
| 1 | Admissions | The door slams, the lamp dies, whispers circle you, something is glimpsed in a strobe | on its own |
| 2 | Day Room | A radio and then a TV switch themselves on; the screen has a message for you | silence the radio, switch off the TV, turn around |
| 3 | Burn Ward | Charred figures that step closer whenever no one is watching them, and the lights keep cutting out | pull the lever on the far wall |
| 4 | Nursery | A lullaby, floating dolls, darkness, small feet | wind the music box and wait |
| 5 | Cold Storage | Hanging bodies that swing when you brush past; the butcher comes for whoever threw the breaker | throw the breaker |
| 6 | Chapel | Each candle you light makes the whispering louder, and the fifth wakes what is under the star | light all five candles |
| 7 | Isolation | A walk past three cells: one inmate hits the bars, one stops crying to watch you, one cell is empty | walk it |
| 8 | Hydrotherapy | The key is at the bottom of a tub of dark water | hold USE to reach in |
| 9 | Staff Room | Something patrols the room and stops right outside your hiding place | hide in the nook, stand still, flashlight off |
| 10 | The Way Out | Alarm, red light, and it is behind you | run |

Every interactive room also opens by itself after a while (`FAILSAFE`), and a scene
that errors opens its door instead of trapping anyone. The ward re-arms itself once
the run is over and the building is empty.

## Who sees what

Everyone, with no setup: the building, lamps, wall writing, floating USE prompts,
monsters, the in-your-face scares and all sound.

With the Starfall HUD enabled you also get screen darkening and vignette, distance fog,
film grain, camera shake, flashes, subtitles and objectives. The chip owner gets this
automatically. Other players either press USE on the small terminal outside the
entrance, or press USE on the chip and accept the permission request.

## Owner chat commands

| Command | Effect |
|---------|--------|
| `!ward reset` | Re-arm the ward immediately |
| `!ward open` | Open every door (if someone gets stuck) |
| `!ward status` | Show which rooms are idle / active / done |

## Tuning

The `CONFIG` table at the top of the script holds everything worth changing:

| Key | Default | Meaning |
|-----|---------|---------|
| `AMBIENT` | `0.32` | Brightness of walls and props: 0 is pitch black, 1 is unshaded |
| `HUD_DARKNESS` | `0.26` | Extra screen darkening for HUD players |
| `LAMP_BRIGHTNESS` | `1.0` | Multiplier for every lamp |
| `LAMP_SHADOWS` | `true` | The lamp in your current room casts shadows (costs some FPS) |
| `FOG`, `FILM_GRAIN` | `true` | HUD effects |
| `VOLUME` | `1.0` | Master volume for the chip's sounds |
| `SNAP_YAW` | `90` | Snap the building's direction to this many degrees (0 = free) |
| `FAILSAFE` | `150` | Seconds before a stuck room opens by itself |
| `RESET_DELAY` / `IDLE_RESET` | `40` / `120` | Re-arm timing after a finished / abandoned run |
| `MAT` | — | Materials for floor, walls, ceiling, partitions and doors |

The interior is lit by the map's own light on darkened surfaces plus the ward's lamps, so
how dark it looks depends on the map. If it is too dark or too bright where you play,
change `AMBIENT` first, then `LAMP_BRIGHTNESS`.

## Troubleshooting

- **"build failed"** — the server refused a prop (usually `sbox_maxprops`). Free some up
  and place the chip again.
- **"N decorations were skipped"** — you were near the hologram limit
  (`sf_holograms_max`, default 200). The rooms still work, with less set dressing.
- **No lamps / no wall writing for one player** — that client has blocked Starfall lights,
  holograms or materials for other people's chips in their Starfall permission settings.
  The rest keeps working.
- **Ground warning in chat** — the area ahead is not level; move to flatter ground.
