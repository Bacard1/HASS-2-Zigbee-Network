# 🏠 HOME ASSISTANT with Two Zigbee Networks via Zigbee2MQTT

[![Donate via PayPal](https://img.shields.io/badge/PayPal-Donate-blue?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)
![Script](https://img.shields.io/badge/logo-yaml-green?logo=yaml)

Build a reliable, scalable, and flexible Zigbee infrastructure in Home Assistant by using **two independent Zigbee networks** managed via **Zigbee2MQTT**, with the goal of improving:
- Coverage and stability
- Scalability for a growing number of devices
- Resilience to hardware or software failures

---

## 📦 Contents

- [🏠 HOME ASSISTANT with Two Zigbee Networks via Zigbee2MQTT](#-home-assistant-with-two-zigbee-networks-via-zigbee2mqtt)
  - [📦 Contents](#-contents)
  - [⚙️ Hardware](#️-hardware)
  - [🛠️ Software \& Integrations](#️-software--integrations)
    - [📦 Adding Zigbee2MQTT Repositories](#-adding-zigbee2mqtt-repositories)
    - [🔌 Zigbee2MQTT Configuration](#-zigbee2mqtt-configuration)
      - [`zigbee2mqtt1` Configuration](#zigbee2mqtt1-configuration)
      - [`zigbee2mqtt2` Configuration](#zigbee2mqtt2-configuration)
      - [Finish Installation](#finish-installation)
      - [Optional: Add Sensors in Home Assistant](#optional-add-sensors-in-home-assistant)

---

## ⚙️ Hardware

|Image|Model|Network Name|Chipset|USB|Wi-Fi|LAN|VPN|
|----|----|----|----|----|----|----|----|
|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|

---

## 🛠️ Software & Integrations

> ⚠️ **NOTE:** You need to have MQTT Broker and Zigbee2MQTT already installed!  
> For installation instructions, see [HERE](https://github.com/Bacard1/HASS-ZigbeeNetwork)

### 📦 Adding Zigbee2MQTT Repositories

To install a second Zigbee2MQTT instance, add the same repository multiple times by adding extra slashes at the end:

|Instance|Add Link|
|----|----|
|zigbee2mqtt1|[![Add Repo](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/)|
|zigbee2mqtt2|[![Add Repo](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt//)|

> 📷 Result:
![Two zigbee2mqtt repos](/img/2repo_zigbee2mqtt.png)

---

### 🔌 Zigbee2MQTT Configuration

> ⚠️ **Before starting:** Create folders and files manually as shown in the image. Do not install the add-ons yet!

![Folder structure](/img/zigbee2mqtt_folder.png)

---

#### `zigbee2mqtt1` Configuration

Create `configuration.yaml` inside the `zigbee2mqtt1` folder and fill in your values:

```yaml
homeassistant:
  enabled: true
advanced:
  network_key:
    - 24
    - 145
    - 6
    - 57
    - 35
    - 6
    - 28
    - 109
    - 51
    - 181
    - 32
    - 238
    - 5
    - 57
    - 10
    - 194
  pan_id: 35048
  ext_pan_id:
    - 47
    - 153
    - 152
    - 123
    - 72
    - 214
    - 6
    - 71
  homeassistant_legacy_entity_attributes: false
  legacy_api: false
  legacy_availability_payload: false
  channel: 11
  transmit_power: 20
  log_level: debug
external_converters: {}
mqtt:
  base_topic: zigbee2mqtt1
  server: ------------------
  user: ------------------
  password: ------------------
  reject_unauthorized: true
serial:
  port: ------------------
  adapter: zstack
frontend:
  enabled: true
  port: 8099
device_options: {}
devices: {}
```

> ⚠️ Replace all `"------------------"` placeholders with your own values.
> Create a Home Assistant user (e.g., "zigbee2") with no admin rights via **Settings → People → Users**.

---

#### `zigbee2mqtt2` Configuration

Create `configuration.yaml` inside the `zigbee2mqtt2` folder:

```yaml
homeassistant:
  enabled: true
advanced:
  network_key:
    - 174
    - 90
    - 55
    - 133
    - 97
    - 210
    - 220
    - 243
    - 42
    - 197
    - 36
    - 174
    - 123
    - 156
    - 47
    - 132
  pan_id: 60218
  ext_pan_id:
    - 193
    - 183
    - 157
    - 129
    - 131
    - 96
    - 95
    - 91
  homeassistant_legacy_entity_attributes: false
  legacy_api: false
  legacy_availability_payload: false
  channel: 12
  transmit_power: 20
  log_level: debug
external_converters: {}
mqtt:
  base_topic: zigbee2mqtt2
  server: "------------------"
  user: "------------------"
  password: "------------------"
  reject_unauthorized: true
serial:
  port: "------------------"
  adapter: zstack
  baudrate: 115200
frontend:
  enabled: true
  port: 8099
device_options:
  legacy: false
version: 4
devices: {}
```

> ⚠️ Again, replace all `"------------------"` fields with valid entries.
> Create a second user if needed for this instance.

---

#### Finish Installation

After configuring the folders:
1. Install the Zigbee2MQTT Add-on from the new repositories.
2. Before launching, update the config path as shown:

|zigbee2mqtt1|zigbee2mqtt2|
|----|----|
|![conf1](/img/z2m_conf1.png)|![conf2](/img/z2m_conf2.png)|

---

#### Optional: Add Sensors in Home Assistant

Append this to your `configuration.yaml`:

```yaml
mqtt:
  sensor:
    - name: Zigbee2mqtt1 Networkmap
      state_topic: zigbee2mqtt1/bridge/response/networkmap
      value_template: "{{ now().strftime('%Y-%m-%d %H:%M:%S') }}"
      json_attributes_topic: zigbee2mqtt1/bridge/response/networkmap
      json_attributes_template: "{{ value_json.data.value | tojson }}"
    - name: Zigbee2mqtt2 Networkmap
      state_topic: zigbee2mqtt2/bridge/response/networkmap
      value_template: "{{ now().strftime('%Y-%m-%d %H:%M:%S') }}"
      json_attributes_topic: zigbee2mqtt2/bridge/response/networkmap
      json_attributes_template: "{{ value_json.data.value | tojson }}"
```

This lets you visualize both Zigbee networks using tools like `zha-network-visualization-card` or through Developer Tools.

---

> 💡 If you liked this project, check out [more of my repositories here](https://github.com/Bacard1?tab=repositories).  
> Got questions or need help? Feel free to reach out!
