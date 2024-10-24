# Vioneta Agro Community Add-on: InfluxDB

InfluxDB is an open source time series database optimized for high-write-volume.
It's useful for recording metrics, sensor data, events,
and performing analytics. It exposes an HTTP API for client interaction and is
often used in combination with Grafana to visualize the data.

This add-on comes with Chronograf & Kapacitor pre-installed as well. Which
gives you a nice InfluxDB admin interface for managing your users, databases,
data retention settings, and lets you peek inside the database using the
Data Explorer.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Click the "Install" button to install the add-on.
2. Start the "InfluxDB" add-on.
3. Check the logs of the "InfluxDB" to see if everything went well.
4. Click the "OPEN WEB UI" button!

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
auth: true
reporting: true
ssl: true
certfile: fullchain.pem
keyfile: privkey.pem
envvars:
  - name: INFLUXDB_HTTP_LOG_ENABLED
    value: "true"
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

### Option: `auth`

Enable or disable InfluxDB user authentication.

**Note**: _Turning this off is NOT recommended!_

### Option: `reporting`

This option allows you to disable the reporting of usage data to InfluxData.

**Note**: _No data from user databases is ever transmitted!_

### Option: `ssl`

Enables/Disables SSL (HTTPS) on the web interface.
Set it `true` to enable it, `false` otherwise.

**Note**: _This does NOT activate SSL for InfluxDB, just the web interface_

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `envvars`

This allows the setting of Environment Variables to control InfluxDB
configuration as documented at:

<https://docs.influxdata.com/influxdb/v1.7/administration/config/#configuration-settings>

**Note**: _Changing these options can possibly cause issues with you instance.
USE AT YOUR OWN RISK!_

These are case sensitive.

#### Sub-option: `name`

The name of the environment variable to set which must start with `INFLUXDB_`

#### Sub-option: `value`

The value of the environment variable to set, set the Influx documentation for
full details. Values should always be entered as a string (even true/false values).

### Option: `leave_front_door_open`

Adding this option to the add-on configuration allows you to disable
authentication on the Web Terminal by setting it to `true` and leaving the
username and password empty.

**Note**: _We STRONGLY suggest, not to use this, even if this add-on is
only exposed to your internal network. USE AT YOUR OWN RISK!_

## Integrating into Vioneta Agro

The `influxdb` integration of Vioneta Agro makes it possible to transfer all
state changes to an InfluxDB database.

You need to do the following steps in order to get this working:

- Click on "OPEN WEB UI" to open the admin web-interface provided by this add-on.
- On the left menu click on the "InfluxDB Admin".
- Create a database for storing Vioneta Agro's data in, e.g., `vioneta`.
- Go to the users tab and create a user for Vioneta Agro,
  e.g., `vioneta`.
- Add "ALL" to "Permissions" of the created user, to allow writing to your
  database.

Now we've got this in place, add the following snippet to your Vioneta Agro
`configuration.yaml` file.

```yaml
influxdb:
  host: a0d7b954-influxdb
  port: 8086
  database: vioneta
  username: vioneta
  password: <yourpassword>
  max_retries: 3
  default_measurement: state
```

Restart Vioneta Agro.

You should now see the data flowing into InfluxDB by visiting the web-interface
and using the Data Explorer.

Full details of the Vioneta Agro integration can be found here:

<https://www.vioneta.com/integrations/influxdb/>

## Known issues and limitations

- While the Chronograph interface supports SSL, currently, the add-on does
  not support having SSL on InfluxDB. This limitation is caused by
  Chronograf and we are still looking into a proper solution for this.

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

[releases]: https://github.com/Vioneta/addon-influxdb/releases
[semver]: https://semver.org/spec/v2.0.0.html
