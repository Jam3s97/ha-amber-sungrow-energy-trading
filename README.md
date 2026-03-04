# Home Assistant: Sungrow SH10RS & Amber Electric Energy Trading

This repository contains the core Home Assistant packages required to integrate a Sungrow SH10RS hybrid inverter and automate dynamic energy trading with Amber Electric.

## 🌟 Features
* **Automated Amber Trading:** Dynamically switches inverter modes based on real-time Amber wholesale pricing.
* **Negative Price Optimisation:** Automatically charges the battery from the grid when buy prices drop below zero.
* **Solar Curtailment:** Stops exporting solar to the grid when feed-in tariffs turn negative.
* **Price Spike Dumping:** Three customisable tier levels to forcefully discharge the battery to the grid during high-price events.
* **Storm Mode:** Forces the battery to charge to 100% and hold it there in preparation for severe weather.

## 🛠️ Hardware & Software Requirements
* **Inverter:** Sungrow SH10RS (Should be compatible with most SHx series).
* **Battery:** Sungrow SBH series.
* **Connection:** Direct LAN connection to the inverter (Wi-Fi dongle Modbus is often too unstable for realtime control).
* **Home Assistant Integrations:** * Modbus (Native HA integration)
  * Amber Electric (Native HA integration)

## ⚙️ Installation Instructions

### 1. Setup Packages
Ensure your Home Assistant `configuration.yaml` is set up to read from a `packages` directory. Add the following to your `configuration.yaml`:

```yaml
homeassistant:
  packages: !include_dir_named packages
