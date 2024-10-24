# Vioneta Agro Community Add-on: AppDaemon

[AppDaemon][appdaemon] is a loosely coupled, multithreaded, sandboxed Python
execution environment for writing automation apps for Vioneta Agro smart Agriculture
automation software. It also provides a configurable dashboard
suitable for wall mounted tablets.

## Installation

The installation of this add-on is pretty straightforward and not different in
comparison to installing any other Vioneta Agro add-on.

1. Click the "Install" button to install the add-on.
2. Start the "AppDaemon" add-on
3. Check the logs of the "AppDaemon" add-on to see if everything went well.

:information_source: Please note, the add-on is pre-configured to connect with
Vioneta Agro. There is no need to create access tokens or to set your
Vioneta Agro URL in the AppDaemon configuration.

This automatic handling of the URL and token conflicts with the
[AppDaemon official documentation][appdaemon]. The official documentation
will state `ha_url` and `token` options are required. For the add-on, however,
this isn't needed.

## Configuration

**Note**: _Remember to restart the add-on when the configuration is changed._

Example add-on configuration:

```yaml
log_level: info
system_packages:
  - ffmpeg
python_packages:
  - PyMySQL
  - Pillow
```

**Note**: _This is just an example, don't copy and past it! Create your own!_

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

These log level also affects the log levels of the AppDaemon.

### Option: `system_packages`

Allows you to specify additional [Alpine packages][alpine-packages] to be
installed to your AppDaemon setup (e.g., `g++`. `make`, `ffmpeg`).

**Note**: _Adding many packages will result in a longer start-up time
for the add-on._

### Option: `python_packages`

Allows you to specify additional [Python packages][python-packages] to be
installed to your AppDaemon setup (e.g., `PyMySQL`. `Requests`, `Pillow`).

**Note**: _Adding many packages will result in a longer start-up time
for the add-on._

#### Option: `init_commands`

Customize your environment even more with the `init_commands` option.
Add one or more shell commands to the list, and they will be executed every
single time this add-on starts.

## AppDaemon and Dashboard configuration

This add-on does not configure the AppDaemon or Dashboard for you.
It does, however, create some sample files to get you started on the first run.

The configuration of the AppDaemon can be found in the add-on configuration
folder of this add-on.

For more information about configuring AppDaemon, please refer to the
extensive documentation they offer:

<http://appdaemon.readthedocs.io/en/latest/>

## Vioneta Agro access tokens and ha_url settings

By default, this add-on ships without a `token` and without the `ha_url`
in the `appdaemon.yaml` config file. **This is not an error!**

The add-on takes care of these settings for you and you do not need to provide
or set these in the AppDaemon configuration.

This automatic handling of the URL and token conflicts with the AppDaemon
official documentation. The official documentation will state `ha_url` and
`token` options are required. For the add-on, these aren't needed.

However, you are free to set them if you want to override, however, in
general usage, that should not be needed and is not recommended for this add-on.

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

Copyright (c) 2021 - 2024 Vioneta

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

[alpine-packages]: https://pkgs.alpinelinux.org/packages
[appdaemon]: https://appdaemon.readthedocs.io
[python-packages]: https://pypi.org/
[releases]: https://github.com/Vioneta/addon-appdaemon/releases
[semver]: http://semver.org/spec/v2.0.0.htm
