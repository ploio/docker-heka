# Portefaix Heka

* Master :
[![Circle CI](https://circleci.com/gh/portefaix/docker-heka/tree/master.svg?style=svg)](https://circleci.com/gh/portefaix/docker-heka/tree/master)

* Develop :
[![Circle CI](https://circleci.com/gh/portefaix/docker-heka/tree/develop.svg?style=svg)](https://circleci.com/gh/portefaix/docker-heka/tree/develop)

![logo](https://raw.githubusercontent.com/1science/docker-alpine/latest/logo.png)

[Alpine Linux][] is a Linux distribution built around musl libc and BusyBox.
This image is based on the official Alpine Linux.

Ports exported are : `4881` and `4352` (Heka Dashboard)
Volume exported is : `/usr/share/heka`


## Usage

    $ docker run -it -p 4881:4881 -p 4352:4352 portefaix/heka:0.10.0b1


To setup an external configuration file use the exported volume : */usr/share/heka/config.toml*


## Supported tags

- `0.10.0b2` [![](https://badge.imagelayers.io/portefaix/heka:0.10.0b2.svg)](https://imagelayers.io/?images=portefaix/heka:0.10.0b2 'imagelayers.io')
- `0.10.0b1` [![](https://badge.imagelayers.io/portefaix/heka:0.10.0b1.svg)](https://imagelayers.io/?images=portefaix/heka:0.10.0b1 'imagelayers.io')


## License

See [LICENSE](LICENSE) for the complete license.


## Changelog

A [ChangeLog.md](ChangeLog.md) is available.


## Contact

Nicolas Lamirault <nicolas.lamirault@gmail.com>


[Alpine Linux]: http://www.alpinelinux.org

[heka]: https://github.com/mozilla-services/heka
