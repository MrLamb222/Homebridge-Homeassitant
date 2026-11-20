# Thin wrapper around the official Homebridge Docker image.
# Home Assistant builds this on the device the first time you install it.
FROM homebridge/homebridge:latest

# Home Assistant OS already runs its own mDNS (Avahi). Turn the image's
# bundled Avahi off so the two don't fight. Homebridge falls back to its
# built-in ciao mDNS responder, which works alongside the host.
# Set to 1 only if HomeKit can't find the bridge.
ENV ENABLE_AVAHI=0
