# Energy Now: is power cheap right now? (Home Assistant)

A clean Home Assistant dashboard that answers one question at a glance: **is electricity cheap right now, and what is
my home costing me per hour?**

![Energy Now dashboard](screenshot.png)

- **One clear status line:** "🔴 Expensive right now · 0.55 €/kWh · 13% above today's average · your home costs € 0.21/h"
- **Price gauge** vs today's average: cheap / normal / expensive / very expensive
- **Cost per hour right now** (net power × price), also when you export
- **Power-flow gauge** and colour-coded tiles for import, export, solar and home usage
- The last 24 hours of price (with today's average) and power
- **Core Home Assistant only**: no HACS, no custom cards. You edit 4 lines.
- Versions for **€, $, £ and A$**, dashboards in **English, Nederlands and Deutsch**

Works with P1/DSMR, HomeWizard, Enphase Envoy, Shelly EM, Emporia Vue, IoTaWatt, SolarEdge or Powerwall for power,
and Tibber, Octopus Agile, Nord Pool, Amber, EnergyZero or any other "price now" sensor.

## Install (± 10 minutes)
1. Make sure `configuration.yaml` has `homeassistant: packages: !include_dir_named packages`.
2. Copy the file for your currency (`energy_now_EUR.yaml`, `_USD`, `_GBP` or `_AUD`) to `/config/packages/`.
3. Edit the four lines under `EDIT THIS` (your net power sensor and price sensor; solar and average price are optional).
4. Check configuration and restart Home Assistant.
5. Create a new dashboard and paste `dashboard.yaml` (or `dashboard_NL.yaml` / `dashboard_DE.yaml`) in the raw configuration editor.

Full step-by-step guide and FAQ: [GUIDE.md](GUIDE.md).

## What's new in 0.2.1
- Dutch and German dashboards (`dashboard_NL.yaml`, `dashboard_DE.yaml`) with local number formatting

## What's new in 0.2
- Status line at the top and a price-vs-average gauge
- Colour-coded flow tiles, cleaner graphs (price with today's average)
- Two new sensors: `sensor.energy_now_average_price`, `sensor.energy_now_price_vs_average`

## Full version
A paid full version is in the works: daily and monthly costs, the cheapest hours today and tomorrow, a standby-power
finder and a battery/solar savings calculator. Want an e-mail when it's ready? Get the free download (and say "yes")
here: **https://payhip.com/b/aomDO**

## Feedback
Found a bug, or is your meter or price provider not working? Please open an issue.

Tested with Home Assistant 2026.11. Version 0.2.1. MIT licensed.
