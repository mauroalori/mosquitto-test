# MQTT AT Commands Guide

This guide explains the MQTT AT commands used for configuring and controlling MQTT communication with an ESP8266 device.

## Command Overview

### 1. MQTT User Configuration
```
AT+MQTTUSERCFG=0,1,"ESP-01","","",0,0,""
```
- Configures the MQTT client settings
- Parameters:
  - `0`: Client ID (0)
  - `1`: Enable MQTT
  - `"ESP-01"`: Client name
  - `""`: Username (empty)
  - `""`: Password (empty)
  - `0`: SSL/TLS disabled
  - `0`: Certificate index
  - `""`: CA certificate (empty)

### 2. MQTT Connection
```
AT+MQTTCONN=0,"192.168.1.49",1883,1
```
- Establishes connection to MQTT broker
- Parameters:
  - `0`: Client ID
  - `"192.168.1.49"`: Broker IP address
  - `1883`: Broker port (default MQTT port)
  - `1`: Keep alive time in seconds

### 3. MQTT Subscribe
```
AT+MQTTSUB=0,"cafetera/state",1
```
- Subscribes to an MQTT topic
- Parameters:
  - `0`: Client ID
  - `"cafetera/state"`: Topic to subscribe to
  - `1`: QoS (Quality of Service) level

### 4. MQTT Publish
```
AT+MQTTPUB=0,"cafetera/state","ESTADO",1,0
```
- Publishes a message to an MQTT topic
- Parameters:
  - `0`: Client ID
  - `"cafetera/state"`: Topic to publish to
  - `"ESTADO"`: Message content
  - `1`: QoS level
  - `0`: Retain flag (0 = don't retain)

## Usage Notes

1. These commands should be sent sequentially in the order shown above
2. Make sure the ESP8266 is properly connected to the network before sending these commands
3. The broker IP address (192.168.1.49) should be replaced with your actual MQTT broker address
4. The topic "cafetera/state" can be modified according to your needs
5. QoS levels (0,1,2) determine the message delivery guarantee:
   - 0: At most once
   - 1: At least once
   - 2: Exactly once

## Example Flow

1. First configure the MQTT client
2. Connect to the MQTT broker
3. Subscribe to receive messages
4. Publish messages as needed 