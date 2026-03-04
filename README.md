# Home Assistant: Sungrow SH10RS & Amber Electric

This repository provides a robust, automated energy trading solution for the **Sungrow SH-RS** series of hybrid inverters (SH5.0RS, SH8.0RS, SH10RS) paired with **Sungrow SBR/SBH** battery storage.

It is specifically designed for **Amber Electric** customers in Australia to capitalise on wholesale price volatility through automated grid-charging, price-spike dumping, and solar curtailment.

---

## 🌟 Key Features

* **Closed-Loop Amber Trading:** Automatically manages inverter states based on real-time wholesale pricing.
* **Tiered Export Dumping:** Three user-definable price tiers (cents/kWh) to forcefully discharge the battery to the grid during high-price events.
* **Negative Price Protection:**
    * **Auto-Charge:** Automatically charges the battery from the grid when wholesale prices drop below $0.00 (Get paid to charge).
    * **Solar Curtailment:** Forces Zero-Export mode when feed-in tariffs turn negative to prevent paying to export solar.
* **Storm Mode:** A one-click override that forces a 100% charge and maintains a full battery reserve in preparation for severe weather.
* **Manual Overrides:** Full manual control via a dropdown menu for Self-Consumption, Max Export, or Grid Charge modes.

---

## 🛠️ Hardware & Software Requirements

### Hardware
* **Inverter:** Sungrow SH10RS (or any SH-RS/SH-RT series hybrid).
* **Battery:** Sungrow SBR (Modular) or SBH series.
* **Connectivity:** **Physical LAN connection** to the inverter is mandatory. The Sungrow Wi-Fi/WiNet-S dongles do not support the high-frequency Modbus polling required for reliable trading.

### Software/Integrations
* [**Sungrow SHx Integration (mkaiser)**](https://github.com/mkaiser/Sungrow-SHx-Inverter-Home-Assistant): This package relies on the specific entity naming convention provided by this integration.
* **Amber Electric Integration:** The official Home Assistant integration.

---

## ⚙️ Installation & Setup

### 1. Integration Setup
Install the **Sungrow SHx** integration via HACS. Ensure your inverter is connected via Ethernet and Modbus is enabled in the Sungrow settings (typically via the iSolarCloud app).

### 2. Package Configuration
Ensure your `configuration.yaml` is set up to use packages:

```yaml
homeassistant:
  packages: !include_dir_named packages
