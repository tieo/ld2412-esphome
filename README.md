# ld2412-esphome

ESPHome config for the LD2412 mmWave presence sensor + a standalone radar dashboard.

## Files

- `ld2412-esphome.yaml` — ESPHome config, exposes all 14 gates with energy + thresholds over API/web
- `ld2412-radar.html` — open in browser, connect to the ESP's IP, see live radar + tune thresholds

## Setup

Copy `secrets.yaml.example` (or just add your own) with `wifi_ssid` and `wifi_password`, then flash:

```
esphome run ld2412-esphome.yaml --device /dev/ttyUSB0
```

After that OTA works. Engineering mode is required for gate energy data — the dashboard enables it automatically.

## Notes

- UART: TX→GPIO17, RX→GPIO16
- Dashboard talks directly to the ESP's web server, no backend needed
- `Light Threshold` gates the hardware OUT pin based on ambient light — set to 0 to ignore it
