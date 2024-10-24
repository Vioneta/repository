# Vioneta Agro Community Add-on: MQTT IO

Exposes general purpose inputs and outputs (GPIO), hardware sensors and serial
devices to an MQTT server. Ideal for single-board computers such as
the Raspberry Pi.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Click the "Install" button to install the add-on.
2. Set the location of the MQTT IO configuration file in the add-on options.
   By default, this will be `/config/mqtt-io/config.yml`.
3. Create the MQTT IO configuration file. For information about the format
   and configuration option, please consult the MQTT IO documentation:
   <https://mqtt-io.app/2.2.6/#/config/scenarios>
4. Start the "MQTT IO" add-on when the configuration is created.
5. Check the logs of the "MQTT IO" add-on to see if everything went well.

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
configuration_file: /config/mqtt-io.yml
log_level: info
```

**Note**: _This is just an example, don't copy and past it! Create your own!_

### Option: `configuration_file`

The `configuration_file` option allows you to configure the configuration
file MQTT IO will use to run. The default is `/config/mqtt-io/config.yml`,
but you change it to something else if you want.

For more information about the MQTT IO configuration file format, see:

<https://mqtt-io.app/2.2.7/#/config/scenarios> and <https://mqtt-io.app/2.2.7/#/config/ha_discovery>

Please note that this configuration file is not created automatically.

### Option: `log_level`

The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

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

[releases]: https://github.com/Vioneta/addon-mqtt-io/releases
[semver]: https://semver.org/spec/v2.0.0.html
