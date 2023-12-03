# SSLH - Windows Cygwin binaries #
- https://github.com/yrutschle/sslh
----
### version [2.0.1](https://github.com/yrutschle/sslh/releases/tag/v2.0.1) - 2023-09-24

**Released 2023-12-03** *(x64 - gcc `11.4.0`)*

-----
### Build Scripts

- [@nono303/win-build-scripts](https://github.com/nono303/win-build-scripts)

### Dependencies

> if you have Cygwin already installed, you don't need `cygwin1.dll`, `cygpcre2-8-0.dll`, `cygev-4.dll`
> Just ensure that you have packages `libpcre2_x` and `libev4` installed and /bin Cygwin path is correctly set in Windows PATH environment variable

- **[libconfig](https://github.com/hyperrealm/libconfig/releases/tag/v1.7.3)** `1.7.3` _(build)_
  - *cygconfig-11.dll*

- **cygwin** `3.4.10` _(cygwin)_
   - *cygwin1.dll*
- **pcre2** `10.42`_(cygwin)_
  - *cygpcre2-8-0.dll*

- **libev** `4.33` _(cygwin)_ :point_up: _only required for **sslh-ev**_
  - *cygev-4.dll*


### Install as a Windows service

You might use `nssm` to install sslh as a Windows service:

1. copy `nssm-2.25.0.exe` in sslh folder or somewhere in a Windows `%PATH%` folder

2. run theses command - **changing absolute path `C:\sslh`** corresponding to your config and `sslh-XX` with your desired version _(`sslh-ev`, `sslh-fork`, `sslh-select`)_

   ```
   nssm-2.25.0.exe install sslh C:\sslh\sslh-XX.exe
   nssm-2.25.0.exe set sslh AppParameters "-FC:/sslh/config/sslh.cfg"
   nssm-2.25.0.exe set sslh AppDirectory C:\sslh
   nssm-2.25.0.exe set sslh AppExit Default Restart
   nssm-2.25.0.exe set sslh AppNoConsole 1
   nssm-2.25.0.exe set sslh AppPriority ABOVE_NORMAL_PRIORITY_CLASS
   nssm-2.25.0.exe set sslh AppStderr C:\sslh\logs\sslh.log
   nssm-2.25.0.exe set sslh AppStopMethodSkip 6
   nssm-2.25.0.exe set sslh AppTimestampLog 1
   nssm-2.25.0.exe set sslh DisplayName sslh
   nssm-2.25.0.exe set sslh ObjectName LocalSystem
   nssm-2.25.0.exe set sslh Start SERVICE_AUTO_START
   nssm-2.25.0.exe set sslh Type SERVICE_WIN32_OWN_PROCESS
   ```

