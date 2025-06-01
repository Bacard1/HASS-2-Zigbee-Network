![BANNER](/img/benner.png)

# 🏠 HOME ASSISTANT mit zwei Zigbee-Netzwerken über Zigbee2MQTT
[![Home Assistant](https://img.shields.io/badge/🏠_Home_Assistant-41BDF5?logo=homeassistant)](https://www.home-assistant.io/) [![Donate via PayPal](https://img.shields.io/badge/PayPal-Donate-blue?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)
![Script](https://img.shields.io/badge/logo-yaml-green?logo=yaml)
[![Български](https://img.shields.io/badge/BG_Български-език-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg
)](BG.md)
[![Deutch](https://img.shields.io/badge/DE_Deutsche-sprache-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg
)](DE.md)
[![English](https://img.shields.io/badge/EN_English-language-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg)](README.md)

HASS-ZigbeeNetwork ist mein persönliches Home-Assistant-Projekt, das zeigt, wie zwei unabhängige Zigbee-Netzwerke über Zigbee2MQTT integriert werden können.
Ziel ist es, eine zuverlässige, flexible und skalierbare Zigbee-Infrastruktur durch die Verwendung mehrerer Koordinatoren (z. B. SLZB-06, Sonoff Dongle 3.0) aufzubauen.
Diese Konfiguration verbessert die Abdeckung, die Geräteverteilung und die Ausfallsicherheit.

✅ Zwei Zigbee-Netzwerke
✅ Zigbee2MQTT-Konfiguration
✅ Verbesserte Leistung und Zuverlässigkeit
✅ Beispiele mit YAML und Automatisierungen

---

## 📦 Inhalt

- [🏠 HOME ASSISTANT mit zwei Zigbee-Netzwerken über Zigbee2MQTT](#-home-assistant-mit-zwei-zigbee-netzwerken-über-zigbee2mqtt)
	- [📦 Inhalt](#-inhalt)
	- [⚙️ Hardware](#️-hardware)
	- [🛠️ Software und Integrationen](#️-software-und-integrationen)
		- [📦 Hinzufügen von Zigbee2MQTT-Repositories](#-hinzufügen-von-zigbee2mqtt-repositories)
		- [🔌 Konfiguration von Zigbee2MQTT](#-konfiguration-von-zigbee2mqtt)
			- [**zigbee2mqtt1:**](#zigbee2mqtt1)
			- [**zigbee2mqtt2:**](#zigbee2mqtt2)
			- [Installation und Navigation des Zigbee2MQTT Add-ons:](#installation-und-navigation-des-zigbee2mqtt-add-ons)

---

## ⚙️ Hardware
|img|model|Netzwerkname|Chipsatz|USB-Anschluss|Wi-Fi|LAN-Anschluss|VPN|
|----|----|----|----|----|----|----|----|
|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|

 
## 🛠️ Software und Integrationen
> [!CAUTION]
> Um fortzufahren, müssen bereits "MQTT Broker" und "Zigbee2MQTT" installiert sein!!!
> Falls Sie "MQTT Broker" und "Zigbee2MQTT" noch nicht installiert haben, finden Sie detaillierte Informationen [HIER](https://github.com/Bacard1/HASS-ZigbeeNetwork)

### 📦 Hinzufügen von Zigbee2MQTT-Repositories
> [!CAUTION]
> Um eine zweite "Zigbee2MQTT"-Instanz zu installieren, müssen Sie das Repository ein zweites, drittes ... Mal hinzufügen!

> [!WARNING]
> Um mehr als ein Repository hinzuzufügen, fügen Sie am Ende des Repository-Links "/" hinzu oder wählen Sie aus der folgenden Tabelle ()

|zigbee2mqtt|zigbee2mqtt1|zigbee2mqtt2|
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt//)|


|zigbee2mqtt3|zigbee2mqtt4|zigbee2mqtt5
|----|----|----|
|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt///)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt////)|[![ADD REPO](/img/button%20ADD%20ADD-ON%20REPOSITORY%20TO%20MY.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https://github.com/zigbee2mqtt/hassio-zigbee2mqtt/////)|

Ergebnis:
![Zwei zigbee2mqtt-Repositories](/img/2repo_zigbee2mqtt.png)

### 🔌 Konfiguration von Zigbee2MQTT

> [!CAUTION]
> Bild 1 zeigt das Verzeichnis, und die Bilder 2 und 3 zeigen die neuen Ordner, die Sie manuell erstellen müssen. <br>
> Installieren Sie die Add-ons nicht vor Erreichen des Schritts [Installation und Navigation des Zigbee2MQTT Add-ons:](#installation-und-navigation-des-zigbee2mqtt-add-ons)

![zigbee2mqtt](/img/zigbee2mqtt_folder.png)

#### **zigbee2mqtt1:**

Im Ordner "zigbee2mqtt1" konfigurieren wir den folgenden Koordinator:

|![SONOFF](/img/Sonoff%20zigbee3.0%20Dongel.png)|SONOFF Zigbee 3.0 USB Dongle Plus|zigbee2mqtt1|CC2652P|✅|❌|❌|❌|
|----|----|----|----|----|----|----|----|

Erstellen Sie eine neue Datei "configuration.yaml" im Ordner "zigbee2mqtt1", die wie folgt aussehen sollte:

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
> Alle Felder mit dem Inhalt "------------------" müssen von Ihnen ausgefüllt werden! <br>
> Für die Erstellung von "user1" folgen Sie diesen Schritten: <br>
> 📁 Schritt 1: Öffnen Sie Home Assistant → Einstellungen → Add-ons → Mosquitto broker → Einstellungen <br>
> ✏️ Schritt 2: Fügen Sie den Benutzer über die Home-Assistant-Oberfläche hinzu <br>
> Gehen Sie zu "Einstellungen" → "Personen" (Settings → People → Users) <br>
> Klicken Sie auf “➕ Benutzer hinzufügen” <br>
> Geben Sie ein: <br>
> Name: zigbee2 <br>
> Benutzername: zigbee2 <br>
> Passwort: nach_Ihrer_Wahl <br>
> Keine Administratorrechte <br>
> 🔒 Dieser Benutzer erhält automatisch Zugriff auf Mosquitto, wenn das Mosquitto Add-on mit customize: active: false konfiguriert ist (Standard).

#### **zigbee2mqtt2:**

Im Ordner "zigbee2mqtt2" konfigurieren wir den folgenden Koordinator:

|![SLZB](/img/SLZB-06p10.png)|SLZB-06p10|zigbee2mqtt2|CC2652P|✅|✅|✅|✅|
|----|----|----|----|----|----|----|----|

Erstellen Sie eine neue Datei "configuration.yaml" im Ordner "zigbee2mqtt2", die wie folgt aussehen sollte:

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
> Alle Felder mit dem Inhalt "------------------" müssen von Ihnen ausgefüllt werden! <br>
> Für die Erstellung von "user2" folgen Sie diesen Schritten: <br>
> 📁 Schritt 1: Öffnen Sie Home Assistant → Einstellungen → Add-ons → Mosquitto broker → Einstellungen <br>
> ✏️ Schritt 2: Fügen Sie den Benutzer über die Home-Assistant-Oberfläche hinzu <br>
> Gehen Sie zu "Einstellungen" → "Personen" (Settings → People → Users) <br>
> Klicken Sie auf “➕ Benutzer hinzufügen” <br>
> Geben Sie ein: <br>
> Name: zigbee2 <br>
> Benutzername: zigbee2 <br>
> Passwort: nach_Ihrer_Wahl <br>
> Keine Administratorrechte <br>
> 🔒 Dieser Benutzer erhält automatisch Zugriff auf Mosquitto, wenn das Mosquitto Add-on mit customize: active: false konfiguriert ist (Standard).

#### Installation und Navigation des Zigbee2MQTT Add-ons:

Standardinstallation des Zigbee2MQTT Add-ons aus dem neu hinzugefügten Repository. Informationen zur Installation des Zigbee2MQTT Add-ons finden Sie [HIER](https://github.com/Bacard1/HASS-ZigbeeNetwork).<br>

> [!CAUTION]
> STARTEN Sie das Zigbee2MQTT Add-on noch NICHT. Ändern Sie den Pfad zur Konfiguration der Anwendung wie im folgenden Bild gezeigt:

|zigbee2mqtt1|zigbee2mqtt2|
|----|----|
|![zigbee2mqtt1](/img/z2m_conf1.png)|![zigbee2mqtt2](/img/z2m_conf2.png)|

> [!CAUTION]
> STARTEN Sie noch NICHT, sondern fügen Sie in die "configuration.yaml" von Home Assistant die folgenden Zeilen ein:

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

Diese MQTT-Sensor-Konfiguration ist die perfekte Möglichkeit, die beiden Zigbee2MQTT-Netzwerke separat in Home Assistant zu visualisieren – besonders wenn Sie sie mit Karten wie zha-network-visualization-card oder einfach über Developer Tools → States → Attribute überwachen möchten.

> [!TIP]
> Wenn Ihnen dieses Projekt gefallen hat, finden Sie [HIER](https://github.com/Bacard1?tab=repositories) weitere interessante Repositories von mir.<br>
> Falls Sie auf Schwierigkeiten stoßen oder Fragen haben, zögern Sie nicht, mich zu kontaktieren.