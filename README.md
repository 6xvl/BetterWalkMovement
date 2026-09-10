# BetterWalkMovement

Stock walking mode in BeamNG.drive feels slow and floaty. This mod tunes the walking
character's movement so it actually starts and stops when you tell it to, and walks
at a normal human pace instead of a shuffle.

## What it changes

It's a single file: `lua/vehicle/controller/playerController.lua`, the same controller
BeamNG ships for the walking character (the "unicycle" vehicle under the hood). The mod
overrides it with these values:

| | Stock | This mod |
|---|---|---|
| Walk speed | 1.8 m/s | 3.2 m/s |
| Sprint speed | 5 m/s | 9 m/s |
| Torque authority | 500 | 950 |
| Max angular velocity (walk / sprint) | 4.5 / 13 | 8 / 23 |
| Accel/decel smoothing | 10 | 30 |

The last one matters most. Stock BeamNG ramps your speed up and down slowly on purpose,
which is where the "gliding" feeling comes from. Bumping the smoothing rate makes the
character actually stop when you let go of the stick instead of coasting for half a
second.

Sprint and camera zoom aren't touched by this mod because they don't need to be.
BeamNG already has `sprintHold` and `cameraZoom` built into the walking character, they're
just unbound by default. Go to Options > Controls, search "sprint", and bind
`sprintHold` to a key (Left Shift is the obvious pick). Do the same for `cameraZoom` and
bind it to your scroll wheel or a spare key.

## Install

1. Download the zip from [Releases](../../releases) or clone this repo.
2. Drop the `lua` folder straight into
   `%LOCALAPPDATA%\BeamNG.drive\current\mods\unpacked\BetterWalkMovement\` (or wherever
   your BeamNG user folder lives), keeping the `lua/vehicle/controller/` structure.
3. Restart BeamNG.
4. Get out of a vehicle and walk around.

If you're not sure where your mods folder is: open BeamNG, go to the mod manager, and
it'll show you the path at the top.

## Why it works this way

BeamNG loads mod files into its virtual filesystem and layers them over the base game
by matching file path. Ship a file at the same path as a stock game file and yours wins.
That's it, no special mod format needed for this kind of change, just the same relative
path the game already uses.

## Tuning it yourself

All the numbers live at the top of `playerController.lua` as plain local variables.
Open it in any text editor, change a number, save, restart BeamNG. No build step.

## License

MIT. Do whatever you want with it.
