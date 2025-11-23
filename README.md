# Corviont Maps – Monaco Demo

Run the Corviont Maps stack locally for a tiny region (Monaco). MapLibre UI, vector tiles, Valhalla routing, and a SQLite-based geocoder - all offline, all in one Docker stack.

## Prerequisites

You’ll need:

- A 64-bit OS (Linux, macOS, or Windows)
- [Docker](https://docs.docker.com/get-docker/) installed
- Docker Compose (included with recent Docker Desktop; if needed, see the [Compose install docs](https://docs.docker.com/compose/install/))

To verify Docker is ready:

```bash
docker version
docker compose version
```

## Quickstart

Clone the repo, start the stack, and open the UI:

```bash
git clone https://github.com/corviont/monaco-demo.git
cd monaco-demo

# Set the port you want the frontend to listen on (3000 is just an example)
export CORVIONT_PORT=3000

docker compose up -d
# Then open http://localhost:$CORVIONT_PORT in your browser
```

To stop the stack:

```bash
docker compose down
```
--- 

## What you get in this demo

Once the stack is up, you have:

### Frontend (MapLibre UI)

- URL: `http://localhost:$CORVIONT_PORT` (for example `http://localhost:3000` if you used the value above).
- A minimal map UI that talks to the local tiles, routing, and search APIs in this stack.

### Tiles API (PMTiles server)

- Serves Monaco vector tiles from a single `.pmtiles` file.
- Used by the MapLibre style in the UI; no external tile servers or map APIs are called.

### Routing API (Valhalla)

- Exposes an HTTP API for offline routing between arbitrary points in Monaco.
- The UI uses it to compute routes; you can also call it directly from your own tools.

### Geocoder API (SQLite + Nominatim data)

- Provides forward and reverse geocoding over HTTP.
- Backed by a SQLite database derived from Nominatim-style data, so all search stays local.

All of these services run as containers on your machine; after the initial image pulls, the demo runs without external map or routing APIs.

## More information

If you’d like more information, or if you’re interested in using Corviont Maps in production:

- Visit the website: **https://www.corviont.com/**
- Or email: **hello@corviont.com**