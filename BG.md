![BANNER](/img/benner.png)

# 🏠 HOME ASSISTANT с две Zigbee мрежи чрез Zigbee2MQTT

[![PayPal дарение](https://img.shields.io/badge/PayPal-Дари-синьо?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)
![Скрипт](https://img.shields.io/badge/logo-yaml-green?logo=yaml)
[![Български](https://img.shields.io/badge/Български-език-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg
)](BG.md)

HASS-ZigbeeNetwork е мой личен проект за Home Assistant, който показва как да се интегрират две независими Zigbee мрежи чрез Zigbee2MQTT.
Целта е да се изгради надеждна, гъвкава и мащабируема Zigbee инфраструктура чрез използването на няколко координиращи адаптера (напр. SLZB-06, Sonoff Dongle 3.0).
Тази конфигурация подобрява покритието, разпределението на устройствата и устойчивостта при сривове.

✅ Две Zigbee мрежи
✅ Zigbee2MQTT конфигурация
✅ Подобрена производителност и надеждност
✅ Примери с YAML и автоматизации

---

## 📦 Съдържание

- [🏠 HOME ASSISTANT с две Zigbee мрежи чрез Zigbee2MQTT](#-home-assistant-с-две-zigbee-мрежи-чрез-zigbee2mqtt)
  - [📦 Съдържание](#-съдържание)
  - [⚙️ Хардуер](#️-хардуер)
  - [🛠️ Софтуер и интеграции](#️-софтуер-и-интеграции)
    - [📦 Добавяне на Zigbee2MQTT хранилища](#-добавяне-на-zigbee2mqtt-хранилища)
    - [🔌 Конфигурация на Zigbee2MQTT](#-конфигурация-на-zigbee2mqtt)
      - [**zigbee2mqtt1:**](#zigbee2mqtt1)
      - [**zigbee2mqtt2:**](#zigbee2mqtt2)
      - [Инсталиране и навигиране на Zigbee2MQTT Add-on:](#инсталиране-и-навигиране-на-zigbee2mqtt-add-on)

---

## ⚙️ Хардуер
|img|model|network name|Чипсет|USB port|Wi-Fi|LAN port|VPN|
|----|----|----|----|----|----|----|----|
|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|

 
## 🛠️ Софтуер и интеграции
> [!CAUTION]
> За да продължите се изисква вече инсталиран "MQTT Broker" и "Zigbee2MQTT"!!!
> Ако нямате инсталиран "MQTT Broker" и "Zigbee2MQTT" можете да намерите подробна информация [ТУК](https://github.com/Bacard1/HASS-ZigbeeNetwork)

### 📦 Добавяне на Zigbee2MQTT хранилища
> [!CAUTION]
> За да инсталирате втора добавна "Zigbee2MQTT" е необходимо да добавите хранилището втори, трети ... пъти!

> [!WARNING]
> За да добавите повече от едно хранилището още веднъж към линка на хранилището добавете "/" в краят на линка или изберете от таблицата по долу ()

|zigbee2mqtt|zigbee2mqtt1|zigbee2mqtt2|
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt//)|


|zigbee2mqtt3|zigbee2mqtt4|zigbee2mqtt5
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt///)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt////)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/////)|

Резултат:
![Две хранилища zigbee2mqtt](/img/2repo_zigbee2mqtt.png)

### 🔌 Конфигурация на Zigbee2MQTT

> [!CAUTION]
> На картината номер 1 показва директорията, а номер 2 и 3 показват новите папки които трябва да създадете ръчно. <br>
> Не инсталирайте предварително добавките преди да стигнете до Стъпката [Инсталиране и навигиране на Zigbee2MQTT Add-on:](#инсталиране-и-навигиране-на-zigbee2mqtt-add-on)

![zigbee2mqtt](/img/zigbee2mqtt_folder.png)

#### **zigbee2mqtt1:**

В папката "zigbee2mqtt1" ще конфигурираме следният координатор.:

|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|----|----|----|----|----|----|----|----|

Създайте нов файл "configuration.yaml" в папката "zigbee2mqtt1" които трябва да изглежда така.:

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
> Всички полета със съдържание "------------------" трябва да бъдат попълнени от вас! <br>
> За създаването на "user1" следвайте тези стъпки: <br>
> 📁 Стъпка 1: Отвори Home Assistant → Настройки → Add-ons → Mosquitto broker → Настройки <br>
> ✏️ Стъпка 2: Добави потребителя от Home Assistant UI <br>
> Отиди в "Настройки" → "Потребители" (Settings → People → Users) <br>
> Натисни “➕ Add user” <br>
> Въведи: <br>
> Име: zigbee2 <br>
> Потребителско име: zigbee2 <br>
> Парола: по_твой_избор <br>
> Без администраторски права <br>
> 🔒 Този потребител автоматично получава достъп до Mosquitto, ако Mosquitto Add-on е конфигуриран с customize: active: false (по подразбиране е така).

#### **zigbee2mqtt2:**

В папката "zigbee2mqtt2" ще конфигурираме следният координатор.:

|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|
|----|----|----|----|----|----|----|----|

Създайте нов файл "configuration.yaml" в папката "zigbee2mqtt2" които трябва да изглежда така.:

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
> Всички полета със съдържание "------------------" трябва да бъдат попълнени от вас! <br>
> Необходимо е  създаването на "user2" следвайте тези стъпки: <br>
> 📁 Стъпка 1: Отвори Home Assistant → Настройки → Add-ons → Mosquitto broker → Настройки <br>
> ✏️ Стъпка 2: Добави потребителя от Home Assistant UI <br>
> Отиди в "Настройки" → "Потребители" (Settings → People → Users) <br>
> Натисни “➕ Add user” <br>
> Въведи: <br>
> Име: zigbee2 <br>
> Потребителско име: zigbee2 <br>
> Парола: по_твой_избор <br>
> Без администраторски права <br>
> 🔒 Този потребител автоматично получава достъп до Mosquitto, ако Mosquitto Add-on е конфигуриран с customize: active: false (по подразбиране е така).

#### Инсталиране и навигиране на Zigbee2MQTT Add-on:

Стандартна инсталация на Zigbee2MQTT Add-on от ново добавеното Repository, информация за инсталирането на Zigbee2MQTT Add-on [ТУК](https://github.com/Bacard1/HASS-ZigbeeNetwork).<br>

> [!CAUTION]
> НЕ СТАРТИРАЙТЕ ВСЕ ОЩЕ Zigbee2MQTT Add-on промени пътят до конфигурацията на приложението както на снимката по долу:

|zigbee2mqtt1|zigbee2mqtt2|
|----|----|
|![zigbee2mqtt1](/img/z2m_conf1.png)|![zigbee2mqtt2](/img/z2m_conf2.png)|

> [!CAUTION]
> НЕ СТАРТИРАЙТЕ ВСЕ ,а добавете в "configuration.yaml" на Home Assistant следните редове:

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

Тази конфигурация на mqtt: сензори е перфектният начин да визуализираш двете Zigbee2MQTT мрежи поотделно в Home Assistant — особено ако искаш да ги следиш чрез карти като zha-network-visualization-card или просто чрез Developer Tools → States → атрибути.

> [!TIP]
> Ако този проект ви е харесъл, [ТУК](https://github.com/Bacard1?tab=repositories) ще намерите още интересни хранилища направени от мен.<br>
> Ако срещате затруднения или имате въпроси не се колебайте да се свържете с мен.