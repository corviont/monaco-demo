# Corviont Maps - Offline Pack (Monaco Sample)

This repo is a small, public **sample pack** for [Corviont Maps](https://www.corviont.com): MapLibre UI, vector tiles, Valhalla routing, and SQLite-based geocoding (search + reverse) - **fully offline**, in one Docker Compose stack.

**No install:** try the [live demo](https://demo.corviont.com/?utm_source=github_demo_top) (Vienna).

![Corviont Monaco demo: offline routing + map + search](gallery.jpg) 

## Need a pack for your hardware / region?

- **Request a pilot** (we'll email a Vienna starter pack so you can test on your hardware): https://www.corviont.com/?utm_source=github_demo_top#request-region
- **Benchmarks:** https://www.corviont.com/blog/hardware-footprint-benchmarks-methodology-and-full-results

## Prerequisites

- 64-bit OS (verified on Ubuntu and Raspberry Pi OS) 
- Docker [installed](https://docs.docker.com/engine/install/) and running, including Docker Compose
Sanity check:

```bash
# x86_64 or aarch64  => OK
uname -m 

# 64 => OK 
getconf LONG_BIT

# should output versions 
docker version
docker compose version
```

## Quickstart

```bash
git clone https://github.com/corviont/monaco-demo.git
cd monaco-demo

# Choose the port
echo "CORVIONT_PORT=3000" > .env

# Optional: allow browser apps from another origin (comma-separated; use "*" to allow all)
echo "CORVIONT_CORS_ALLOWED_ORIGINS=http://localhost:3001" >> .env

docker compose up -d
```

Open in your browser:

- http://localhost:3000 (replace 3000 if you changed `CORVIONT_PORT`)

Stop:
```bash
docker compose down
```
> Running on another machine? Replace `localhost` with the device IP/hostname.

## What you get

Once the stack is up, it exposes a single HTTP entrypoint on `CORVIONT_PORT`:

- **UI ([MapLibre](https://github.com/maplibre/maplibre-gl-js)):** `/`
- **Tiles ([go-pmtiles](https://github.com/protomaps/go-pmtiles)):** `/tiles/...` (served from a single PMTiles file)
- **Routing ([Valhalla](https://github.com/valhalla/valhalla)):** `/router/route` (other Valhalla endpoints may exist but are experimental)
- **Geocoding:** `/geocoder/search` and `/geocoder/reverse`

After the initial image pulls, the demo runs without any external map/routing APIs.

## Docs
Install + troubleshooting + API + copy-paste examples:
https://www.corviont.com/docs

## Request a pilot

Monaco is a tiny public sample pack. To evaluate Corviont on your hardware, [request a pilot](https://www.corviont.com/?utm_source=github_demo_bottom#request-region) or email hello@corviont.com.