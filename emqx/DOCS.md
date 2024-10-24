# Vioneta Agro Community Add-on: EMQX

[EMQX][emqx] is an Open-source MQTT broker with a high-performance real-time
message processing engine, powering event streaming for IoT devices at massive
scale. As the most scalable MQTT broker, EMQX can help you connect any device,
at any scale (including your home).

The [EMQX MQTT broker][emqx] is an advanced alternative to the Mosquitto MQTT
broker/add-on that is generally used in Vioneta Agro. It has a UI
to configure, manage, and debug your MQTT broker, clients, and traffic.

While EMQX sells their product mainly as a cloud hosted product on their
website, this add-on runs EMQX in a fully local, self-hosted environment.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Click the "Install" button to install the add-on.
2. Start the "EMQX" add-on.
3. Check the logs of the "EMQX" to see if everything went well.
4. Open the Web UI.
5. Log in with the default credentials: username `admin` and password `public`.
6. Be sure to first set up authentication in for your MQTT client, but setting
   up an authentication method in the EMQX web UI under "Access Control" ->
   "Authentication".
7. Read the step above again and **make sure** you have set up authetication.

_Notes:_

- When configuring Vioneta Agro, Zigbee2MQTT or any other MQTT application
  or client on your Vioneta Agro machine to connect to eMQX, use
  `a0d7b954-emqx` as the broker/hostname to connect to.
  In some cases, just `localhost` will work as well.
- When connecting external devices to your EMQX add-on, use the IP address or
  hostname of your Vioneta Agro instance as the broker/hostname to connect to.

## Configuration

You most likely don't need these configuration options. Almost all
configuration can be done via the web UI that is available in this add-on.
Some more advanced/complex configuration options are not available in the
web UI, but can be configured using this option (for example, when
setting up clustering of multiple instances).

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
env_vars:
  - name: EMQX_NODE__NAME
    value: "something@else.local"
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

### Option: `env_vars`

This option allows you to tweak every aspect of EMQX by setting
configuration options using environment variables. See the example at the
start of this chapter to get an idea of how the configuration looks.

For more information about using these variables, see the official EMQX
documentation:

<https://www.emqx.io/docs/en/v5.0/admin/cfg.html>

**Note**: _Only environment variables starting with `EMQX_` are accepted.\_

## Known issues and limitations

- This add-on cannot run simultaneously with the Mosquitto add-on.
- EMQX uses ports 1883, 8083, 8084, and 8883 by default. It is possible
  one of your existing add-ons conflicts with that. In such cases, either
  change the ports of the other add-on or change the listner ports of EMQX.
  To change the ports of EMQX, you will need to temporary stop the conflicting
  add-on, as you need to access the EMQX web UI to change the listner ports.
- The WebRTC integration by AlexxIT is known to cause a port conflict on
  port 8083. Temporary disabling the integration (similar as the point above
  for add-ons) can be used to allow accessing the EMQX web UI to adjust the
  listeners.

## Changelog & Releases

This repository keeps a change log using [GitHub's releases][releases]
functionality.

Releases are based on [Semantic Versioning][semver], and use the format
of `MAJOR.MINOR.PATCH`. In a nutshell, the version will be incremented
based on the following:

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.

## License

MIT License

Copyright (c) 2023-2024 Vioneta

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[emqx]: https://www.emqx.io/
[releases]: https://github.com/Vioneta/addon-emqx/releases
[semver]: https://semver.org/spec/v2.0.0.html
