# 🏠 HOME ASSISTANT with two zigbee networks via zigbee2mqtt

[![PayPal donation](https://img.shields.io/badge/PayPal-donation-синьо?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)
![Script](https://img.shields.io/badge/logo-yaml-green?logo=yaml)

Building a reliable, scales and flexible Zigbee infrastructure in Home Assistant using two independent Zigbee networks managed by ZigBee2MQTT to improve:
- Coverage and stability
- Scaleness in a growing number of devices
- Sustainability in possible hardware or software crashes

---

## 📦 Content

- [🏠 Smart home with two zigbee networks via zigbee2mqtt](#-smart-home-with-two-zigbee-networks-via-zigbee2mqtt)
  - [📦 Content](#-content)
  - [⚙️ Hardware](#️-hardware)
  - [🛠️ Software and integration](#️-software-and-integration)
    - [📦 Adding Zitgee2MQT storage](#-adding-zitgee2mqt-storage)
    - [🔌 Configuration на Zigbee2MQTT](#-configuration-на-zigbee2mqtt)
      - [**zigbee2mqtt1:**](#zigbee2mqtt1)
      - [**zigbee2mqtt2:**](#zigbee2mqtt2)
      - [Installing and navigating Zigbee2mqtt Add-on:](#installing-and-navigating-zigbee2mqtt-add-on)
	
---
S
## ⚙️ Hardware
|img|model|network name|Chipset|USB port|Wi-Fi|LAN port|VPN|
|----|----|----|----|----|----|----|----|
|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|

## 🛠️ Software and integration
> [!CAUTION]
> To continue, "MQTT Broker" and "Zigbee2MQT" are required !!!
> If you do not have "MQTT Broker" and "Zigbee2MQT" installed you can find detailed information [Here](https://github.com/Bacard1/HASS-ZigbeeNetwork)

### 📦 Adding Zitgee2MQT storage
> [!CAUTION]
> To install a second added "Zitgee2MQT" you need to add the repository second, third ... times!

> [!WARNING]
> To add more than one repository once more to the storage link add "/" at the end of the link or select from the plate below 

|zigbee2mqtt|zigbee2mqtt1|zigbee2mqtt2|
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt//)|

|zigbee2mqtt3|zigbee2mqtt4|zigbee2mqtt5
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt///)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt////)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/////)|

Result:
![Two Zigbee2mqtt storage facilities](/img/2repo_zigbee2mqtt.png)

### 🔌 Configuration на Zigbee2MQTT

> [!CAUTION]
> The number 1 shows the directory, and number 2 and 3 show the new folders you need to create manually.<br>
> Do not pre -install the supplements before reaching the step [Installation and navigating Zigbee2MQTT Add-on:](#инсталиране-и-навигиране-на-zigbee2mqtt-add-on)

![zigbee2mqtt](/img/zigbee2mqtt_folder.png)

#### **zigbee2mqtt1:**

In the "Zigbee2MQTT 1" folder, we will configure the following coordinator.:

|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|----|----|----|----|----|----|----|----|

Create a new file "Configuration.yaml" in the "Zigbee2MQTT1" folder which should look like this.:

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
> All fields with content "----------------" must be filled by you!<br>
> To create "user1" follow these steps: <br>
> 📁 Step 1: Open Home Assistant → Settings → Add-Aons → Mosquitto Broker → Settings <br>
> ✏️ Step 2: Add user from Home Assistant UI <br>
> Go to "Settings" → "Users" (Settings → People → Users) <br>
> Press “➕ add user” <br>
> Enter: <br>
> Name: Zigbee2 <br>
> Username: Zigbee2 <br>
> Password: By time_ selection <br>
> No Administrative Rights <br>
> 🔒 This user automatically gets access to Mosquitto if Mosquitto Add-on is configured with Customize: Active: False (by default is).

#### **zigbee2mqtt2:**

In the "Zigbee2MQTT 2" folder, we will configure the following coordinator.:

|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|
|----|----|----|----|----|----|----|----|

Create a new file "Configuration.Yaml" in the "Zigbee2MQTT2" folder which should look like this.:

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
> All fields with content "----------------" must be filled by you!<br>
> You need to create "user2" Follow these steps: <br>
> 📁 Step 1: Open Home Assistant → Settings → Add-Aons → Mosquitto Broker → Settings <br>
> ✏️ Step 2: Add user from Home Assistant UI <br>
> Go to "Settings" → "Users" (Settings → People → Users) <br>
> Press “➕ add user” <br>
> Enter: <br>
> Name: Zigbee2 <br>
> Username: Zigbee2 <br>
> Password: By time_ selection <br>
> No Administrative Rights <br>
> 🔒 This user automatically gets access to Mosquitto if Mosquitto Add-on is configured with Customize: Active: False (default is).

#### Installing and navigating Zigbee2mqtt Add-on:

Standard installation of Zigbee2MQTT Add-on from the new added Repository, Information on Installing the Zigbee2MQTT Add-on [Here](https://github.com/Bacard1/HASS-ZigbeeNetwork).<br>

> [!CAUTION]
> Do not start the Zigbee2MQTT Add-On Change the Road to the Application of the App as in the photo below:

|zigbee2mqtt1|zigbee2mqtt2|
|----|----|
|![zigbee2mqtt1](/img/z2m_conf1.png)|![zigbee2mqtt2](/img/z2m_conf2.png)|

> [!CAUTION]
> Do not start all the time, but add to "Configuration.yaml" to Homesssistant the following lines:

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

This MQTT: Sensor configuration is the perfect way to visualize the two Zigbee2mqt networks separately in Home Assistant-especially if you want to follow them through cards like Zha-Network-Visualization-Card or simply via Developer Tools → States → Init.

> [!TIP]
> If you liked this project, [HERE](https://github.com/bacard1?tab=repositories) you will find more interesting borders made by me. <br>
> If you have difficulty or have questions, do not hesitate to contact me.
