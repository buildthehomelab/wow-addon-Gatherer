# Gatherer for clients with Project Reforged HD's extra zone maps

[Gatherer](http://www.gathereraddon.com) 3.1.16 by Norganna's AddOns for the WoW 3.3.5a client, with map data for the extra zone maps that Project Reforged HD adds.

Gatherer remembers where you gathered herbs, ore and treasure and shows those spots on your minimap and world map.

## Why this copy

Project Reforged HD's patch-M adds 53 maps to Kalimdor and the Eastern Kingdoms: starting areas such as Northshire Valley and Ammen Vale, and caves such as Fargodeep Mine and Fel Rock. On a client with those maps, stock Gatherer doesn't know them, so every login it:

- opens a "Gatherer was unable to identify the following zones" warning, and
- prints an "Astrolabe is missing data for ..." line in chat for each map.

This copy knows those maps, so both are gone, and the minimap code has a real size for each of them instead of zero.

## Changes from Gatherer 3.1.16

The first commit is the unmodified 3.1.16 release. Everything after it is from this fork:

- `Gatherer/Astrolabe/Astrolabe.lua`: size and position of the 53 added maps, computed from the client's map bounds.
- `Gatherer/GatherZoneTokens.lua`: a zone token for each added map. The token is the map's file name, which is what stock Gatherer already saved nodes under, so nodes you gathered there before keep working.
- `Gatherer/Gatherer.toc`: `## Interface: 30300`, so the 3.3.5a client doesn't mark the addon out of date.
- The `Load.xml` files and two Configator XML files declare the `xsi` prefix they use.

On a stock 3.3.5a client the added entries are simply unused, and Gatherer works as before.

## Patch Notes: Gatherer
Category: Addons

- **Gatherer** is now available in the launcher's Addons list. It remembers where you gathered herbs, ore and treasure and shows those spots on your minimap and world map.
- This version knows the starting-area and cave maps that Project Reforged HD adds, so it no longer opens a zone warning or fills the chat with missing-data lines at login.
> If you already have Gatherer installed, your gathered nodes are kept.

## Requirements

- A WoW 3.3.5a (12340) client. The added map data is for clients with Project Reforged HD's extra zone maps; stock clients are unaffected.

## Installation

With [Portalkeeper](https://github.com/buildthehomelab/wow-Portalkeeper) (the buildthehomelab fork), turn on **Gatherer** in the Addons list if your realm offers it.

By hand: copy the `Gatherer` folder into `Interface/AddOns`, so you end up with `Interface/AddOns/Gatherer/Gatherer.toc`, replacing any Gatherer folder already there. Your gathered nodes are stored in `WTF`, not in the addon folder, so they are kept.

## Troubleshooting

- **"Astrolabe is missing data" lines are still printed:** another addon with its own copy of Astrolabe loads before Gatherer. The lines come from that addon's copy.
- **"LibMapData-1.0 is missing data" lines:** these come from a different addon. Gatherer doesn't use LibMapData.

## Credits

- Gatherer: [Norganna's AddOns](http://www.gathereraddon.com)
- Astrolabe: Esamynn
- Map data for the Project Reforged HD zone maps: [buildthehomelab](https://github.com/buildthehomelab)

## License

Gatherer is released under the [GNU General Public License v2](LICENSE) or later, with the exception described in the source headers. Astrolabe is released under the GNU Lesser General Public License (`Gatherer/Astrolabe/lgpl.txt`).
