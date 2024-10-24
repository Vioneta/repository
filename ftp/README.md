# Vioneta Agro Community Add-on: FTP

[![Release][release-shield]][release] ![Project Stage][project-stage-shield] ![Project Maintenance][maintenance-shield]

A secure and fast FTP server for Vioneta Agro

## About

The FTP protocol might be come in handy sometimes. While old,
it still has its use. For example, most IP Cameras still support the upload
of images or videos via FTP.

This add-on provides an FTP Server for Vioneta Agro in a reasonably secure manner.
While FTP is not entirely secure by its (unencrypted) nature, this add-on
supports FTP over SSL (FTPS) and jails (chroot) the virtual users in their
home directories.

Of course, if you'd really want to, you could also use this add-on to again
access to your Vioneta Agro configuration via FTP.

[maintenance-shield]: https://img.shields.io/maintenance/yes/2024.svg
[project-stage-shield]: https://img.shields.io/badge/project%20stage-production%20ready-brightgreen.svg
[release-shield]: https://img.shields.io/badge/version-v5.1.1-blue.svg
[release]: https://github.com/Vioneta/addon-ftp/tree/v5.1.1
