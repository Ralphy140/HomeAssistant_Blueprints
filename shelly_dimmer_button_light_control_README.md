# Zigbee2MQTT Button – Shelly Dimmer Light Control

Control a dimmable light using a Zigbee2MQTT button device. Designed for single-button remotes paired with a Shelly Dimmer or any dimmable light — single press toggles the light, hold dims up or down, and double press jumps to full brightness.

[![Import Blueprint](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FRalphy140%2FHomeAssistant_Blueprints%2Fblob%2Fmain%2Fshelly_dimmer_button_light_control.yaml)

---

## Requirements

- **Zigbee2MQTT** installed and running
- A Zigbee button device paired via Zigbee2MQTT (e.g. IKEA, Aqara, Sonoff, Tuya)
- A dimmable light entity (e.g. Shelly Dimmer, Zigbee dimmer, Hue bulb)

---

## Button Actions

| Button Action | Result |
|---|---|
| **Single press** (light is off) | Turn light on at last brightness |
| **Single press** (light is on) | Turn light off |
| **Hold** (brightness below threshold) | Dim up in steps until released |
| **Hold** (brightness above threshold) | Dim down in steps until released |
| **Release** | Stop dimming |
| **Double press** | Turn on at full brightness (100%) |

---

## Configuration Options

| Option | Description | Default |
|---|---|---|
| **Button Device** | Your Zigbee2MQTT button device | *(required)* |
| **Light Entity** | The dimmable light to control | *(required)* |
| **Brightness Threshold** | Level (0–255) that decides dim up vs dim down on hold | `128` |
| **Brightness Step (%)** | How much brightness changes per step while holding | `5%` |
| **Dim Up Delay (ms)** | Time between steps when dimming up | `300ms` |
| **Dim Down Delay (ms)** | Time between steps when dimming down | `250ms` |

---

## How to Import

### Option 1 — One-click import (recommended)

Click the **Import Blueprint** button at the top of this page. You'll be taken to your Home Assistant instance where you can preview and confirm the import.

### Option 2 — Manual import via URL

1. In Home Assistant, go to **Settings → Automations & Scenes → Blueprints**
2. Click **Import Blueprint** (blue button, bottom right)
3. Paste the following URL:

```
https://github.com/Ralphy140/HomeAssistant_Blueprints/blob/main/shelly_dimmer_button_light_control.yaml
```

4. Click **Preview**, then **Import**

---

## Creating an Automation from this Blueprint

Once imported:

1. Go to **Settings → Automations & Scenes → Blueprints**
2. Find **Zigbee2MQTT Button – Shelly Dimmer Light Control**
3. Click **Create Automation**
4. Select your button device and light entity
5. Adjust any optional settings as desired
6. Save the automation

---

## Notes

- This blueprint uses **device triggers** via the MQTT integration, so the button must be set up as a device in Zigbee2MQTT with device actions available in Home Assistant
- The automation runs in **restart** mode — if a hold starts while another action is running, it will restart cleanly
- The brightness threshold (default 128, which is ~50%) means: if the light is dim, holding will brighten it; if it's already bright, holding will dim it. Adjust this to taste.

---

## Changelog

| Version | Date | Notes |
|---|---|---|
| 1.0 | 2026-03-19 | Initial release |
