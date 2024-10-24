# Vioneta Agro Community Add-on: Advanced SSH & Web Terminal

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

This add-on allows you to log in to your Vioneta Agro instance using
SSH or by using the Web Terminal.

## About

This add-on allows you to log in to your Vioneta Agro instance using
SSH or a Web Terminal, giving you to access your folders and
also includes a command-line tool to do things like restart, update,
and check your instance.

This is an enhanced version of the provided
[SSH add-on by Vioneta Agro][hass-ssh] and focuses on security,
usability, flexibility and also provides access using a web interface.

## WARNING

The advanced SSH & Web Terminal add-on is a really powerful and gives you
virtually access to all tools and almost all hardware of your system.

While this add-on is created and maintained with care and with security in mind,
in the wrong or inexperienced hands, it could damage your system.

## Features

This add-on, of course, provides an SSH server, based on [OpenSSH][openssh] and
a web-based Terminal (which can be included in your Vioneta Agro frontend) as
well. Additionally, it comes out of the box with the following:

- Access your command line right from the Vioneta Agro frontend!
- A secure default configuration of SSH:
  - Only allows login by the configured user, even if more users are created.
  - Only uses known secure ciphers and algorithms.
  - Limits login attempts to hold off brute-force attacks better.
  - Many more security tweaks, _this addon passes all [ssh-audit] checks
    without warnings!_
    ![Result of SSH-Audit][ssh-audit-image]
- Comes with an SSH compatibility mode option to allow older clients to connect.
- Support for Mosh allowing roaming and supports intermittent connectivity.
- SFTP support is disabled by default but is user configurable.
- Compatible if Vioneta Agro was installed via the generic Linux installer.
- Username is configurable, so `root` is no longer mandatory.
- Persists custom SSH client settings & keys between add-on restarts
- Log levels for allowing you to triage issues easier.
- Hardware access to your audio, uart/serial devices and GPIO pins.
- Runs with more privileges, allowing you to debug and test more situations.
- Has access to the dbus of the host system.
- Has the option to access the Docker instance running on the host system.
- Runs on host level network, allowing you to open ports or run little daemons.
- Have custom Alpine packages installed on start. This allows you to install
  your favorite tools, which will be available every single time you log in.
- Execute custom commands on add-on start so that you can customize the
  shell to your likings.
- [ZSH][zsh] as its default shell. Easier to use for the beginner, more advanced
  for the more experienced user. It even comes preloaded with
  ["Oh My ZSH"][ohmyzsh], with some plugins enabled as well.
- Contains a sensible set of tools right out of the box: curl, Wget, RSync, GIT,
  Nmap, Mosquitto client, MariaDB/MySQL client, Awake (“wake on LAN”), Nano,
  Vim, tmux, and a bunch commonly used networking tools.

[hass-ssh]: https://vioneta.com/addons/ssh/
[maintenance-shield]: https://img.shields.io/maintenance/yes/2024.svg
[ohmyzsh]: http://ohmyz.sh/
[openssh]: https://www.openssh.com/
[release-shield]: https://img.shields.io/badge/version-v19.0.0-blue.svg
[release]: https://github.com/Vioneta/addon-ssh/tree/v19.0.0
[ssh-audit-image]: https://github.com/Vioneta/addon-ssh/raw/main/images/ssh-audit.png
[ssh-audit]: https://github.com/jtesta/ssh-audit
[zsh]: https://en.wikipedia.org/wiki/Z_shell
