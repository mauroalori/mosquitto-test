# MQTT Test Environment

This repository contains configuration and commands for testing MQTT communication using Mosquitto.

## Docker Container Setup

To start the Mosquitto broker in a Docker container:

```bash
docker run -it --rm \
  -p 1883:1883 \
  -p 9001:9001 \
  -v $(pwd)/mosquitto.conf:/mosquitto/config/mosquitto.conf \
  eclipse-mosquitto
```

This command:
- Runs the official Eclipse Mosquitto image
- Maps port 1883 (default MQTT port)
- Mounts the local `mosquitto.conf` file into the container
- Removes the container when stopped (`--rm`)

## Testing MQTT Communication

### Subscribe to a Topic

To subscribe to the "test/topic" and listen for messages:

```bash
mosquitto_sub -h localhost -t cafetera/state
```

### Publish a Message

To publish a message to "test/topic":

```bash
mosquitto_pub -h localhost -t cafetera/state -m "Hola desde mosquitto_pub"
```

## Notes

- Make sure you have the `mosquitto-clients` package installed on your system to use the `mosquitto_sub` and `mosquitto_pub` commands
- The broker must be running before you can publish or subscribe
- Default port is 1883
- Localhost is used as the broker address in these examples 