# Homebridge add-on

Runs the official `homebridge/homebridge` Docker image on Home Assistant OS.

- Web UI: `http://<home-assistant-ip>:8581` (or the **Open Web UI** button)
- Config, plugins and HomeKit pairings: the add-on's config folder
  (`/addon_configs/<id>_homebridge/` over Samba, mounted as `/homebridge`
  inside the container)

## First start

1. Install and start the add-on, then open the web UI.
2. Follow the setup wizard on first visit to create your admin account.
3. Scan the QR code in the UI with the Home app to pair the bridge.
4. Install plugins from the UI, for example `homebridge-unifi-protect` for
   UniFi cameras and the doorbell.

## Moving an existing Homebridge

Stop the old one first (two copies with the same bridge identity will fight).
Copy its `config.json`, `persist/` and `accessories/` folders into this
add-on's config folder before the first start. Keeping `persist/` keeps your
HomeKit pairings, so you don't have to re-add the bridge or your devices.

## If HomeKit can't find the bridge

The add-on turns off the image's bundled Avahi (`ENABLE_AVAHI=0` in the
Dockerfile) because Home Assistant OS already runs one. If discovery fails,
edit the Dockerfile to `ENABLE_AVAHI=1`, then rebuild the add-on.

## Updates

The add-on tracks the `latest` image. Use **Rebuild** on the add-on page to
pull the newest Homebridge. Updates made inside the web UI are replaced when
the container is rebuilt, which is normal for the Docker image.
