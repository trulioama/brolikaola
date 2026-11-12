# StarfallEx chips

| Chip | What it is |
|------|------------|
| [`horror_room.txt`](horror_room.txt) | **WARD 13** — a ten-room, walk-through horror house |
| [`apocalypse.txt`](apocalypse.txt) | **APOCALYPSE** — a slow, map-wide storm with a face in the sky and a tornado ([jump to it](#apocalypse--the-face-in-the-storm)) |

Both need [StarfallEx](https://github.com/thegrb93/StarfallEx) only and use stock Garry's Mod /
Half-Life 2 content. Copy the file into `garrysmod/data/starfall/`, open it in the Starfall
editor and place the chip with the Starfall processor tool.

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
  about 15–40 seconds the first time on a map (every model has to load, and the chip paces
  itself to stay inside StarfallEx's CPU quota). Progress and "ready" are printed in chat.
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

- **"CPU usage exceeded"** — the chip waits for its CPU average to drop before every
  spawn, so this should not happen from building. If you run other heavy chips at the same
  time they share your quota (`sf_timebuffer`); remove them or raise the quota.
- **"build failed"** — the server refused a prop (usually `sbox_maxprops`). Free some up
  and place the chip again.
- **"N decorations were skipped"** — you were near the hologram limit
  (`sf_holograms_max`, default 200). The rooms still work, with less set dressing.
- **No lamps / no wall writing for one player** — that client has blocked Starfall lights,
  holograms or materials for other people's chips in their Starfall permission settings.
  The rest keeps working.
- **Ground warning in chat** — the area ahead is not level; move to flatter ground.

# APOCALYPSE — the face in the storm

One chip that ends the world slowly, on whatever map you are on. Place it anywhere under open
sky and type `!apoc start` (or press USE on it).

## What happens

| Time | Stage | What you see and hear |
|------|-------|-----------------------|
| 0:00 | Dusk | The sky sinks to a deep navy. Three cloud decks arrive from one horizon, band by band, sink into place and begin to turn around the zenith. Wind rises |
| 0:45 | Storm | Sheet lightning low on the horizon with thunder seconds later, then nearer and louder; forked bolts hit the ground, sometimes close to a player. Rain from 1:35 |
| 2:30 | The face | A glow gathers behind the clouds, then an enormous head pushes forward through the deck, nose and brow first. It blinks, its eyes dart ahead of its head, it looks around the map, picks a player and stares without blinking, and from 3:28 it laughs |
| 3:56 | The tornado | It draws breath, purses its lips and blows a column of vapour at the map. Where that lands, a wall cloud lowers, dust starts to turn on the ground, and a funnel comes down to meet it. It then wanders the map, leaning into its own movement, and grows; every further breath feeds it and shoves it downwind |

After that it runs until you stop it: lightning, new looks, stares, laughs and breaths are
decided as it goes, so no two runs are the same. `!apoc stop` lets the funnel rope out, the face
sink back and the sky clear over 30 seconds, then removes everything.

## Commands (chip owner)

| Command | Effect |
|---------|--------|
| `!apoc start` | Begin (USE on the chip does the same while idle) |
| `!apoc stop` | Clear the storm gracefully, then clean up |
| `!apoc reset` | Remove everything immediately |
| `!apoc status` | Stage, elapsed time, tornado strength |
| `!apoc skip` | Jump to the next stage |
| `!apoc laugh` / `!apoc blow` | Make the face do it now (once it is out) |

## Who sees what

Everyone, with no setup: sky, clouds, lightning, the face, the tornado, rain, and all sound. It is
built from clientside holograms, custom meshes and particles, so it needs no HUD permission and
puts no entities on the server. Timing, lightning, the face's behaviour and the tornado's path
come from the server, so all players see the same event.

With the Starfall HUD you also get camera shake (thunder, laughter, the tornado nearby) and a
screen flash on lightning. The owner gets this automatically; other players press USE on the
chip and accept the request.

## Tuning

`CONFIG` at the top of the script:

| Key | Default | Meaning |
|-----|---------|---------|
| `TIME_SCALE` | `1.0` | `2` runs the build-up twice as fast |
| `DARKNESS` | `0.68` | How dark the world gets (0 – 0.85). The sky keeps its look whatever you set |
| `SKY_DISTANCE` | `9000` | Radius of the storm sky around each player. Lower it on maps that clip distant geometry |
| `FACE_SIZE` | `1.0` | Size of the head |
| `FACE_MODEL` | `models/gman_high.mdl` | Any character model with an `eyes` attachment and the standard face flexes |
| `EYE_TRACKING` | `true` | Eye movement independent of the head |
| `QUALITY` | `1.0` | Cloud, funnel and debris density (0.5 – 1.5) |
| `RAIN` | `true` | Rain particles and rain sound |
| `TORNADO_PHYSICS` | `true` | The tornado throws the physics props this chip may touch (normally the owner's) |
| `HUD_EFFECTS` | `true` | Camera shake and screen flash for HUD players |
| `VOLUME` | `1.0` | Master volume |
| `END_TIME` | `30` | Seconds `stop` takes to clear the sky |
| `AUTO_START` | `false` | Start as soon as the chip is placed |
| `ADMINS_CAN_CONTROL` | `false` | Let server admins use the commands too |

Budget per player: 61 holograms (of 200), 20 materials (of 40), 17 sounds (of 20), 3 particle
emitters. If another of your chips already uses most of a budget, the pieces that do not fit
are skipped and the rest still runs.

## How it works, and what that means

- **The sky belongs to each player.** Dome, clouds and face are placed around your own eyes
  like a skybox, so they are the same size and in the same compass direction for everyone,
  wherever they stand. The tornado, ground strikes and debris are at real places on the map.
- **The world is darkened by a tint, not relit.** Starfall cannot change a map's baked lighting,
  so the ground gets darker and bluer but shadows stay where the map put them.
- **The face is a real character head** with its flex controllers driven every frame, which is
  what gives it blinking, eye darts and lip shapes. When StarfallEx's `bass` library can read
  the laugh sound, the jaw follows its measured loudness; otherwise it follows the laugh's rhythm.
- **Maps with heavy fog or a short far clip plane** hide distant things, including this. If the
  sky or the face is cut off, lower `SKY_DISTANCE`.
- **Indoor-only maps** have no sky to show it in. The chip tells you if it found none.

## Troubleshooting

- **"X switched off: …" in chat** — one part hit an error and disabled itself; the rest keeps
  running. `!apoc reset` then `!apoc start` rebuilds everything. Please report the message.
- **"CPU usage exceeded"** — building is spread over frames and the chip skips work when its
  average is high, but other heavy chips share your quota. Lower `QUALITY`.
- **One player sees or hears nothing** — they have blocked holograms, materials, meshes or
  sounds for other people's chips in their Starfall permission settings.
- **The eyes look wrong with a custom `FACE_MODEL`** — set `EYE_TRACKING = false`.
