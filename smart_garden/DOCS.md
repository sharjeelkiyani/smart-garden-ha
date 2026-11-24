# Smart Garden

Smart irrigation that runs inside Home Assistant: up to 32 zones on ESPHome relay boards or Zigbee
valves, schedules that follow sunrise, weather (Open-Meteo) and soil-moisture rules, a water budget,
frost and rain skips, indoor plants, lawn care and feeding reminders.

## Before you start
- Install the **Mosquitto broker** add-on (Settings → Add-ons → Add-on store). Smart Garden finds it
  by itself. With it, your **Zigbee2MQTT** devices are available to Smart Garden, and Smart Garden's
  zones, sensors and controls appear in Home Assistant automatically (MQTT integration).
- Valves: an ESPHome relay board with `web_server:` (one relay at a time + its own cut-off timer is
  strongly recommended), or Zigbee valves.

## Install
1. Settings → Add-ons → Add-on store → ⋮ → **Repositories** → add
   `https://github.com/sharjeelkiyani/smart-garden-ha`
2. Find **Smart Garden**, **Install**, then **Start**. Turn on **Show in sidebar**.
3. Open **Garden** in the sidebar - you're signed in with your Home Assistant user.
4. **Devices** page: add your relay board (or let it find it on your network), match relays to zones,
   pick your soil / rain / temperature sensors. Set your town under Settings → Smart watering.

## Options
| Option | Meaning |
|---|---|
| `ha_users_are_admins` | Home Assistant users get full control (on) or can only water and look (off) |
| `zone_count` | Zones created on first start (1-8); more can be added in the app |
| `esphome_url` | Optional: your relay board's address (e.g. `http://192.168.1.50`) - or add it on the Devices page |
| `esphome_entity_pattern` | Relay names on the board, e.g. `Irrigation Relay Zone{n}` |
| `zigbee2mqtt_base_topic` | Zigbee2MQTT's base topic (default `zigbee2mqtt`) |
| `timezone` | Only if different from Home Assistant's |

## In Home Assistant
A device named after your garden with: a switch per zone (on = water for its default minutes, off =
stop), soil moisture and minutes watered per zone, every sensor, what's watering, time left, next run,
water today, rain, relay boards online, automatic watering on/off, Stop all and Run buttons per
schedule. Everything still goes through Smart Garden's safety limits (one zone at a time, maximum
minutes). A ready-made dashboard is under Settings → Home Assistant in the app.

## Backups
Everything is in the add-on's data folder, included in Home Assistant backups.

## Supported
Home Assistant OS or Supervised on 64-bit: Raspberry Pi 3/4/5 (aarch64) and x86-64 (amd64).
