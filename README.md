# vaultwarden-build-win
(Unofficial) vaultwarden pre-built binaries for windows

I use Python as a build script; `.bat` would be fine, but I can't write one.

## Tips for building in a local environment
To build in a local environment, install the following libraries: 

- mysqlclient.lib (This repository uses mysqlclient that comes with MySQL 9.3)
- libpq (This repository uses PostgreSQL17's libpq)
- sqlite3.lib (a pre-created version is included in this repository, but you can also install Visual Studio and create your own)
- OpenSSL

It is preferable to use Git Bash when building (environment variables can be passed at the same time as the commands).

Environment variables to be passed at build time:
```
SQLITE3_LIB_DIR="(Directory with sqlite3.lib)"
MYSQLCLIENT_VERSION="(MySQL version with mysqlclient bundled)"
MYSQLCLIENT_LIB_DIR="(MySQL Location)\MySQL\MySQL Server 9.3\lib"
OPENSSL_DIR="(Path of the directory containing the OpenSSL lib and include subdirectories)"
PQ_LIB_DIR="(Directory with libpq)"
```

The commands are the same as those listed in the [wiki](https://github.com/dani-garcia/vaultwarden/wiki/Building-binary).

Example is:
```bash
SQLITE3_LIB_DIR="F:\apps\developer\lib\sqlite3" MYSQLCLIENT_VERSION="9.3" MYSQLCLIENT_LIB_DIR="F:\apps\developer\MySQL\MySQL Server 9.3\lib" OPENSSL_DIR="F:\apps\scoop\apps\openssl\current" PQ_LIB_DIR="C:\Program Files\PostgreSQL\17\lib" cargo build --features sqlite,mysql,postgresql --release
```
