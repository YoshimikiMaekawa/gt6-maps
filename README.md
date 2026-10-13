# gt6-maps

Offline map data for the GT6 Pulse Tracks running app, one file per Japanese prefecture (`<prefecture>.gt6map`). Each file holds a basemap, a walking/running road network and a place index for that prefecture.

The files are published on the [maps release](../../releases/tag/maps) and rebuilt monthly from open data. This repository contains only that open data. It holds no code and no personal data.

## Download

`https://github.com/YoshimikiMaekawa/gt6-maps/releases/download/maps/<prefecture>.gt6map`

The prefecture IDs are `hokkaido`, `aomori`, …, `tokyo`, `kanagawa`, …, `okinawa` (romanised names, 47 in total).

Remote islands that can only be reached by ferry or plane, such as the Izu Islands, Ogasawara and Tsushima, are not included.

## Format

A `.gt6map` file is a ZIP archive containing:

| File | Contents |
|---|---|
| `manifest.json` | Size and SHA-256 of each file, the bounding box, the license and the attribution |
| `basemap.pmtiles` | Vector map tiles ([PMTiles](https://github.com/protomaps/PMTiles) v3) |
| `graph.sqlite` | Walkable road network (SQLite) |
| `places.sqlite` | Place names, facilities and block-level addresses (SQLite) |

## Sources and licenses

### OpenStreetMap: roads, facilities, place names and prefecture boundaries

© OpenStreetMap contributors. Available under the [Open Database License (ODbL) 1.0](https://opendatacommons.org/licenses/odbl/1-0/). See https://www.openstreetmap.org/copyright.

`graph.sqlite` and `places.sqlite` are derived databases of OpenStreetMap. They are made available under the ODbL 1.0. Their contents can be extracted from the ZIP as they are.

The OSM data was taken from the [Geofabrik](https://download.geofabrik.de/asia/japan.html) regional extracts.

### Protomaps basemap: map tiles (`basemap.pmtiles`)

Cut out of the [Protomaps](https://protomaps.com/) basemap builds. These are an ODbL Produced Work and require OpenStreetMap attribution: © OpenStreetMap contributors.

### 国土交通省 位置参照情報: block-level addresses (`places.sqlite`, table `blocks`)

「街区レベル位置参照情報 国土交通省」（令和6年度 24.0a 版、`<都道府県コード>000-24.0a.zip`）を gt6-pulse-tracks が加工して作成。

- Source: https://nlftp.mlit.go.jp/isj/
- Terms of use: [位置参照情報利用約款](https://nlftp.mlit.go.jp/isj/agreement.html)
- Processing: one representative point is kept per block, and names are normalised for search.
- Per the terms of use, this data cannot be used for surveying that requires high accuracy, or for certification.

## Disclaimer

The data is provided as is, with no guarantee of accuracy or completeness. Map data can be out of date. Check the actual roads and facilities on site.
