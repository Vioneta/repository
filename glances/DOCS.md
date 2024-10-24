# Vioneta Agro Community Add-on: Glances

Glances is a cross-platform monitoring tool which aims to present a maximum of
information in a minimum of space through a Web-based interface.

Glances can export all system statistics to InfluxDB, allowing you to look
at all your system information and its behavior over time.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Click the "Install" button to install the add-on.
2. Disable "Protection mode" in the add-on panel.
3. Start the "Glances" add-on.
4. Check the logs of the "Glances" to see if everything went well.
5. Click the "OPEN WEB UI" button take a glance at Glances.

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
process_info: false
refresh_time: 10
ssl: false
certfile: fullchain.pem
keyfile: privkey.pem
influxdb:
  enabled: false
  host: a0d7b954-influxdb
  port: 8086
  interval: 60
  ssl: false
  prefix: localhost
  version: 1 # Either 1 or 2

  # Version 1
  username: glances
  password: "!secret glances_influxdb_password"
  database: glances

  # Version 2
  token: "!secret glances_influxdb2_token"
  bucket: glances
  org: myorg
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

### Option: `process_info`

If set to `true`, it will enable the process module of Glances and gives
detailed insight into each individual process running on the system.

**Note**: _Enabling this feature will increase CPU usage significantly._

### Options: `refresh_time`

Sets refresh time (in seconds).

**Note**: _Refreshing more quickly will result in a higher CPU usage._

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the Glances Web UI. Set it `true` to enable it,
`false` otherwise.

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option group `influxdb`

---

The following options are for the option group: `influxdb`. These settings
only apply to the Glances InfluxDB data export.

#### Option `influxdb`: `enabled`

Enables/Disables the Glances data export to InfluxDB.

#### Option `influxdb`: `host`

The hostname where InfluxDB is running.

**Note**: _If you are using the Community InfluxDB add-on,
use `a0d7b954-influxdb` as the hostname._

#### Option `influxdb`: `port`

The port on which InfluxDB is listening.

#### Option `influxdb`: `interval`

Defines the interval (in seconds) on how often Glances exports data to InfluxDB.

#### Option `influxdb`: `ssl`

Adding this option will allow SSL to be used on the InfluxDB connection. If not
set will default to `false` which is the required setting for the Community
InfluxDB add-on.

#### Option `influxdb`: `prefix`

The hostname to append for exported data.

**Note**: _For the Grafana Glances dashboard set this to `localhost`._

#### Option `influxdb`: `version`

The influxdb version to connecting. Either **1** or **2**.

#### Option `influxdb`: `username`

> Applied to version 1 only

The username that you have created for Glances to authenticate against
InfluxDB.

#### Option `influxdb`: `password`

> Applied to version 1 only

The password for the above username option.

#### Option `influxdb`: `database`

> Applied to version 1 only

The name of the database to store all Glances information into.

If using Influx v2 the config value must be configured but will be ignored.

**Note**: _It is strongly recommended to create a separate database for glances
and not store this in the same database name as Vioneta Agro._

#### Option `influxdb`: `token`

> Applied to version 2 only

An InfluxDB token with permissions to write to the given bucket. This should
look like `t9iHPiGQyg0ds4K1IlBrCyBsNGh71dkdR6u8Y9eeR37UzfGuFukFCdbMI4YA9EtKb4zr5coFXKw67tbBEP7CPw==`

#### Option `influxdb`: `bucket`

> Applied to version 2 only

The name of the bucket to store all Glances information into.

**Note**: _It is strongly recommended to create a separate bucket for glances
and not store this in the same bucket as Vioneta Agro._

#### Option `influxdb`: `org`

> Applied to version 2 only

The InfluxDB organization that owns the given bucket.

## Adding Glances as a sensor into Vioneta Agro

The Vioneta Agro Glances sensor platform is consuming the system information
provided by the Glances API.

This enables one to track and display their stats in Vioneta Agro,
and even build automations based on that data.

Set up the integration through **Settings -> Devices & Services -> Integrations -> Add integration -> Glances**.

**Note**: _Once the add-on is running, add the integration with all
defaults, except for port, which should be 61209_

More information about the Glances sensor platform can be found in the
Vioneta Agro documentation:

<https://www.vioneta.com/integrations/glances/>

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

Copyright (c) 2019-2024 Vioneta

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

[releases]: https://github.com/Vioneta/addon-glances/releases
[semver]: https://semver.org/spec/v2.0.0.html
