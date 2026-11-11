# Energy Now (lite): guide

A clean Home Assistant dashboard that answers one question at a glance: **is power cheap right now?**
- cheap, normal, expensive or negative price, with a simple tip;
- what your home is **costing you per hour** right now;
- import, export, solar and home usage;
- the last 24 hours in a graph.

Core Home Assistant only: no HACS and no custom cards. Version 0.1, tested with Home Assistant 2026.11.

## What you need
1. **A net power sensor** (W or kW): positive when importing, negative when exporting. For example:
   - a **P1 / smart meter** reader (DSMR, HomeWizard P1): *Power consumption* or *Active power*;
   - an **Enphase Envoy** with CTs: *Current net power consumption*;
   - **Shelly EM / Shelly Pro 3EM**, **IoTaWatt**, **Emporia Vue**, **SolarEdge** or a **Tesla Powerwall** (*Site power*).
2. **A price-now sensor** (all-in, per kWh): **Tibber**, **Octopus Energy** (Agile), **Nord Pool**, **Amber Electric**,
   **EnergyZero**, **Frank Energie**, **ANWB**, or any other integration that gives the current price.
3. Optional: a **solar power** sensor and an **average price today** sensor. The average enables the cheap/expensive tip and the price gauge (EnergyZero, Nord Pool and Tibber provide one; otherwise create a statistics helper).

## Install (± 10 minutes)
1. Pick the file for your currency: `energy_now_EUR.yaml`, `energy_now_USD.yaml`, `energy_now_GBP.yaml` or `energy_now_AUD.yaml`.
2. Make sure `configuration.yaml` contains:
   ```yaml
   homeassistant:
     packages: !include_dir_named packages
   ```
3. Create the folder `packages` next to `configuration.yaml` and put the file in it.
4. Open the file and edit **only** the four lines under `EDIT THIS`. Find your sensor IDs in
   **Settings → Devices & services → Entities**: search for "power" or "price" and copy the entity ID.
5. **Developer tools → YAML → Check configuration**, then restart Home Assistant.
6. **Settings → Dashboards → Add dashboard → New dashboard**, open it, ⋮ → **Edit** → ⋮ → **Raw configuration editor**,
   paste `dashboard.yaml` and save.

## What the numbers mean
| On the dashboard | Meaning |
|---|---|
| From grid (+) / to grid (−) | Plus: you are buying power. Minus: you are exporting. |
| Costing you per hour | Net power × price now. With a dynamic tariff and no net metering, this is what you really pay (or earn). |
| Home uses | Net + solar: what your home itself is using. |
| Tip | Cheap = at least 10% below today's average, expensive = at least 10% above, negative = below zero. |

## FAQ
- **I have separate import and export sensors.** Create one template sensor "net = import − export"
  (Settings → Helpers → Template sensor) and use it as `source_net`.
- **"No price known".** Check that `source_price` gives a price per kWh and is not "unavailable".
- **My price is in cents.** Create a template sensor that divides by 100, or ask us. The next version handles this.
- **The graphs are empty.** They fill up by themselves; after a day you see 24 hours.

## Remove
Delete the package file and the dashboard, then restart Home Assistant.

---
Questions or problems? Reply to your download e-mail and we'll help.
