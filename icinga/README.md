# Icinga1 & Icinga2 monitoring tool
> Icinga Core has 2 web UI's: Icinga Classical UI and Icinga Web. The latter
requires IDOUtils (a database).

## Prerequisites
- [Apache][1]
- GCC compiler
- C/C++ development libraries
- [GD][2] development libraries
- libdbi/libdbi-drivers, database like MySQL or PostgreSQL [for [IDOUtils][4]]
- Download [Icinga Monitoring plugins][3]

## Installing Icinga Core with [Classic UI][5]
To build from source (no IDOUtils required)

```sh
./configure \
  --with-command-group=icinga-cmd \
  --disable-idoutils \
  --with-systemd-unit-dir=/usr/lib/systemd/system \
  --with-systemd-sysconfig-dir=/etc/rc.conf
```

### Installing [Icinga Web 1.x][6]

```sh
./configure
  --prefix=/usr/local/icinga-web
  --with-web-user=www-data
  --with-web-group=www-data
  --with-web-path=/icinga-web
  --with-web-apache-path=/etc/apache2/conf.d
  --with-db-type=mysql
  --with-db-host=localhost
  --with-db-port=3306
  --with-db-name=icinga_web
  --with-db-user=icinga_web
  --with-db-pass=icinga_web
  --with-conf-dir=etc/conf.d
  --with-log-dir=log
  --with-api-subtype=TYPE DB driver or network connection
  --with-api-host=HOST Host to connect (DB or other) (default localhost)
  --with-api-port=PORT Port for connection (default 3306)
  --with-api-socket=PATH Path to socket (default none)
```

#### Where are my [config files][7]?
```sh
tree -d -L 1 app/modules/AppKit/
app/modules/AppKit/
|-- actions
|-- config
|-- lib
|-- models
|-- templates
|-- validate
|-- views
```

[1]: http://www.apache.org/
[2]: http://www.boutell.com/gd/
[3]: https://www.monitoring-plugins.org/
[4]: https://docs.icinga.com/latest/en/quickstart-idoutils.html
[5]: https://docs.icinga.com/latest/en/quickstart-icinga.html
[6]: https://docs.icinga.com/latest/en/icinga-web-scratch.html
[7]: https://docs.icinga.com/latest/en/icinga-web-config.html
