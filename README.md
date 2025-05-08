![BANNER](/img/benner.png)

# 🏠 HOME ASSISTANT with Two Zigbee Networks via Zigbee2MQTT

[![Donate via PayPal](https://img.shields.io/badge/PayPal-Donate-blue?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)
![Script](https://img.shields.io/badge/logo-yaml-green?logo=yaml)
[![Български](https://img.shields.io/badge/Български-език-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg
)](BG.md)

Building a reliable, scalable, and flexible Zigbee infrastructure in Home Assistant using two independent Zigbee networks managed by Zigbee2MQTT, to improve:
- Coverage and stability
- Scalability with an increasing number of devices
- Resilience against potential hardware or software failures

---

## 📦 Table of Contents

- [🏠 HOME ASSISTANT with Two Zigbee Networks via Zigbee2MQTT](#-home-assistant-with-two-zigbee-networks-via-zigbee2mqtt)
  - [📦 Table of Contents](#-table-of-contents)
  - [⚙️ Hardware](#️-hardware)
  - [🛠️ Software and Integrations](#️-software-and-integrations)
    - [📦 Adding Zigbee2MQTT Repositories](#-adding-zigbee2mqtt-repositories)
    - [🔌 Zigbee2MQTT Configuration](#-zigbee2mqtt-configuration)
      - [**zigbee2mqtt1:**](#zigbee2mqtt1)
      - [**zigbee2mqtt2:**](#zigbee2mqtt2)
      - [Installing and Navigating the Zigbee2MQTT Add-on:](#installing-and-navigating-the-zigbee2mqtt-add-on)

---

## ⚙️ Hardware
|img|model|network name|Chipset|USB port|Wi-Fi|LAN port|VPN|
|----|----|----|----|----|----|----|----|
|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|

## 🛠️ Software and Integrations
> [!CAUTION]
> You must already have "MQTT Broker" and "Zigbee2MQTT" installed to continue!!!
> If you don't have "MQTT Broker" and "Zigbee2MQTT" installed, detailed information can be found [HERE](https://github.com/Bacard1/HASS-ZigbeeNetwork)

### 📦 Adding Zigbee2MQTT Repositories
> [!CAUTION]
> To install a second Zigbee2MQTT add-on, you need to add the repository a second, third... time!

> [!WARNING]
> To add the same repository more than once, append a "/" at the end of the repository URL or select from the table below:

|zigbee2mqtt|zigbee2mqtt1|zigbee2mqtt2|
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt//)|


|zigbee2mqtt3|zigbee2mqtt4|zigbee2mqtt5
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt///)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt////)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/////)|

_Result:_
![Two zigbee2mqtt repositories](/img/2repo_zigbee2mqtt.png)

### 🔌 Zigbee2MQTT Configuration

> [!CAUTION]
> In the image, number 1 shows the directory, and numbers 2 and 3 show the new folders you need to create manually. <br>
> Do not install the add-ons before reaching the step [Installing and Navigating the Zigbee2MQTT Add-on:](#installing-and-navigating-the-zigbee2mqtt-add-on)

![zigbee2mqtt](/img/zigbee2mqtt_folder.png)

#### **zigbee2mqtt1:**

In the "zigbee2mqtt1" folder we will configure the following coordinator:

|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|----|----|----|----|----|----|----|----|

Create a new file "configuration.yaml" in the "zigbee2mqtt1" folder which should look like this:

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

> [!CAUTION]
> All fields containing "------------------" must be filled in by you! <br>
> To create "user1", follow these steps: <br>
> 📁 Step 1: Open Home Assistant → Settings → Add-ons → Mosquitto broker → Settings <br>
> ✏️ Step 2: Add the user from the Home Assistant UI <br>
> Go to "Settings" → "People → Users" <br>
> Click “➕ Add user” <br>
> Enter: <br>
> Name: zigbee2 <br>
> Username: zigbee2 <br>
> Password: your_choice <br>
> No admin rights <br>
> 🔒 This user automatically gets access to Mosquitto if the Mosquitto Add-on is configured with customize: active: false (default setting).

#### **zigbee2mqtt2:**

In the "zigbee2mqtt2" folder we will configure the following coordinator:

|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|
|----|----|----|----|----|----|----|----|

Create a new file "configuration.yaml" in the "zigbee2mqtt2" folder which should look like this:

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

> [!CAUTION]
> All fields containing "------------------" must be filled in by you! <br>
> To create "user2", follow these steps: <br>
> 📁 Step 1: Open Home Assistant → Settings → Add-ons → Mosquitto broker → Settings <br>
> ✏️ Step 2: Add the user from the Home Assistant UI <br>
> Go to "Settings" → "People → Users" <br>
> Click “➕ Add user” <br>
> Enter: <br>
> Name: zigbee2 <br>
> Username: zigbee2 <br>
> Password: your_choice <br>
> No admin rights <br>
> 🔒 This user automatically gets access to Mosquitto if the Mosquitto Add-on is configured with customize: active: false (default setting).

#### Installing and Navigating the Zigbee2MQTT Add-on:

Standard installation of the Zigbee2MQTT Add-on from the newly added Repository, installation info can be found [HERE](https://github.com/Bacard1/HASS-ZigbeeNetwork).<br>

> [!CAUTION]
> DO NOT START Zigbee2MQTT Add-on yet — change the configuration path of the application as shown in the image below:

|zigbee2mqtt1|zigbee2mqtt2|
|----|----|
|![zigbee2mqtt1](/img/z2m_conf1.png)|![zigbee2mqtt2](/img/z2m_conf2.png)|

> [!CAUTION]
> DO NOT START YET — instead, add the following lines to Home Assistant's "configuration.yaml":

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

This mqtt: sensor configuration is the perfect way to visualize both Zigbee2MQTT networks separately in Home Assistant — especially if you want to monitor them via cards like zha-network-visualization-card or just through Developer Tools → States → attributes.

> [!TIP]
> If you liked this project, you can find more interesting repositories made by me [HERE](https://github.com/Bacard1?tab=repositories).<br>
> If you encounter difficulties or have questions, don't hesitate to contact me.
