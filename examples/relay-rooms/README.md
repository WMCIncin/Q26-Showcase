# Relay Rooms

By **Bill Kosche - William Kosche**.

Relay Hall has two connected bays, two coloured teleport pads and two player starts. Relay Annex is a single room with a raised central platform. Both maps were designed for this showcase.

## Use the map pack

Place the PK3 in the appropriate game directory of a test profile on a compatible Quake III–based client. Use a lawfully obtained engine and game data. Open the console and run `/map q26_relay_hall` or `/map q26_relay_annex`.

Relay Hall’s cyan and amber pads each lead to a matching end of the other bay. The hall also has a doorway connecting both bays. Open [the floor plan](relay-plan.webp) to see the pad and destination positions.

## Use the example configurations

- `exec q26_relay_rotation.cfg` sets a two-map rotation. An operator can run `vstr nextmap` to advance to the other map.
- `exec q26_relay_subworlds.cfg` loads Relay Hall as the primary map and Relay Annex at `4096 0 0` on versions of Q26 that support immutable subworlds. It uses static geometry for the annex. The hall’s existing pads remain within Relay Hall. Use a fresh test session for each example so latched settings from one do not carry to the other.

## Rebuild the maps

Use the classic Q3Map console compiler from an authorized source. The example was tested with a Q26-compatible build of this compiler. Copy this example's `baseq3` to an empty working directory named `quake3`, keeping its maps, scripts and textures together. Open a shell in that directory.

```text
q3map -threads 1 baseq3/maps/q26_relay_hall.map
q3map -vis -threads 1 baseq3/maps/q26_relay_hall.map
q3map -light -threads 1 baseq3/maps/q26_relay_hall.map
q3map -threads 1 baseq3/maps/q26_relay_annex.map
q3map -vis -threads 1 baseq3/maps/q26_relay_annex.map
q3map -light -threads 1 baseq3/maps/q26_relay_annex.map
```

Use the compiler executable name appropriate for your installation. In PowerShell prefix a local, non-PATH executable with `./`, or invoke its absolute path. The compiler uses the sample’s `scripts/shaderlist.txt` to find its material definitions. For your own map project, add `q26_relay` to your existing shader list.

A PK3 is a ZIP archive. Put the two compiled BSPs under `maps/`, `q26_relay.shader` under `scripts/`, the five tiles under `textures/q26_relay/` and the two config files at the archive root. The ready-made pack also includes the sample licence.

Both configurations also passed a dedicated-server load with networking disabled. The Windows OpenGL client also loaded the exact release PK3 and walked both coloured pads. Cyan landed in the east bay and amber in the west bay. Both produced BSPs use version 46, contain lightmaps and visibility records, and reference the bundled materials. The example does not require the terrain test assets.

The map and material source and their compiled outputs are covered by the BSD Zero Clause licence in [LICENSE.txt](LICENSE.txt).
