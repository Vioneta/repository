# Vioneta Agro Community Add-on: chrony

An NTP server accessible by all hosts on the local network, useful for setting
time on devices with controlled internet access (such as cameras).
The addon can also be used to set the system clock.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Click the "Install" button to install the add-on.
2. Start the "chrony" add-on
3. Check the logs of the "chrony" add-on to see if everything went well.

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
set_system_clock: true
mode: pool
ntp_pool: pool.ntp.org
ntp_server:
  - 54.39.13.155
  - briareus.schulte.org
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

### Option: `set_system_clock`

The `set_system_clock` option configures chrony to set the local system clock.
For some systems it may be preferable to use a different mechanism for
setting the system time.

### Option: `mode`

The `mode` option configures chrony to use either `pool` or `server` mode.
These options are:

- `pool`: References a pool of servers such as pool.ntp.org (Recommended).
- `server`: References a list of specific names or addresses.

Based on the mode the `ntp_pool` or `ntp_server` option will be used.

### Option: `ntp_pool`

Used by pool mode and configures the pool name to be used, should be a DNS
record with multiple entries. The application will select which to reference.

### Option: `ntp_server`

Used by server mode, an array of server names or IP Addresses used as the
time source. The application will select which to reference.

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

[releases]: https://github.com/Vioneta/addon-chrony/releases
[semver]: http://semver.org/spec/v2.0.0.htm
