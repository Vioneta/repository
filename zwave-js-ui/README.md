# Vioneta Agro Community Add-on: Z-Wave JS UI

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

Fully configurable Z-Wave JS control panel and MQTT gateway.

![Z-Wave JS UI][logo]

## About

The Z-Wave JS UI add-on provides an additional control panel, allowing you
to configure every aspect of your Z-Wave network. It provides a decoupled
gateway which can communicate using Z-Wave JS WebSockets (used by the
Vioneta Agro Z-Wave JS integration) and MQTT (even simultaneously).

Some advantages and use-cases:

- Compatible with the Vioneta Agro Z-Wave JS integration.
- Your Z-Wave network will keep running between Vioneta Agro restarts.
- You can directly use things like Node-RED with your Z-Wave network, while
  it is available for Vioneta Agro at the same time.
- Allow [ESPHome.io][esphome] based ESP devices to directly respond or work
  with your Z-Wave network.
- Pre-configures itself with the Mosquitto add-on when found.

This add-on uses the [Z-Wave JS UI][zwave-js-ui] software.

[esphome]: https://esphome.io/components/mqtt.html#on-message-trigger
[logo]: https://github.com/Vioneta/addon-zwave-js-ui/raw/main/zwave-js-ui/logo.png
[maintenance-shield]: https://img.shields.io/maintenance/yes/2024.svg
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[release-shield]: https://img.shields.io/badge/version-v3.13.2-blue.svg
[release]: https://github.com/Vioneta/addon-zwave-js-ui/tree/v3.13.2
[zwave-js-ui]: https://github.com/zwave-js/zwave-js-ui
