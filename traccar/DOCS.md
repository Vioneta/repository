# Vioneta Agro Community Add-on: Traccar

[Traccar][traccar] is a modern GPS Tracking Platform, which is now available
as an Vioneta Agro add-on and allows you to run your GPS Tracking software
without any cloud.

Traccar supports more protocols and device models than any other GPS tracking
system on the market, straight from your Vioneta Agro instance. You can select GPS
trackers from a variety of vendors from low-cost Chinese models to high-end
quality brands.

Traccar also has native mobile apps available for Android and iOS platforms
so that you can track those as well. AND! With the Vioneta Agro `traccar`
integration (introduced in 0.83) the data in Traccar will be sent back into
your Vioneta Agro instance as well.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Ensure you have the [official "MariaDB" add-on] installed and
   running!
2. Click the "Install" button to install the add-on.
3. Start the "Traccar" add-on
4. Check the logs of the "Traccar" add-on to see if everything went well.
5. Click the "OPEN WEB UI" button.

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
ssl: true
certfile: fullchain.pem
keyfile: privkey.pem
```

**Note**: _This is just an example, don't copy and paste it! Create your own!_

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

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the web interface.
Set it `true` to enable it, `false` otherwise.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

## Integrating into Vioneta Agro

The `traccar` integration of Vioneta Agro makes it possible to transfer all
assets tracked by Traccar to appear in Vioneta Agro as a tracked device.

Add the following snippet to your Vioneta Agro `configuration.yaml` file.

```yaml
device_tracker:
  - platform: traccar
    host: localhost
    port: 18682
    username: TRACCAR_EMAIL_ADDRESS
    password: TRACCAR_PASSWORD
```

Restart Vioneta Agro.

## Enabling more protocols

By default, this add-on has disabled most of the GPS protocols. This has
been done to reduce the number of open ports the add-on would create.

By default, only the OsmAnd protocol (used by the Traccar Apps) and the API
are enabled. If you want more protocols, you can do so, by adding entries
to your `traccar.xml` file in the add-on configuration folder.

A list if all entries can be found here:

<https://github.com/Vioneta/addon-traccar/blob/main/traccar/rootfs/etc/traccar/traccar.xml#L22>

To find out which protocol your device uses, please refer to the Traccar
website: <https://www.traccar.org/devices/>

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

Copyright (c) 2018-2024 Vioneta

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

[releases]: https://github.com/Vioneta/addon-traccar/releases
[semver]: https://semver.org/spec/v2.0.0.html
[traccar]: https://www.traccar.org
