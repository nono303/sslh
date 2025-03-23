# SSLH - Windows Cygwin binaries #
- https://github.com/yrutschle/sslh
- https://github.com/nono303/win-build-scripts
----
### Version [2.1.4.37](https://github.com/yrutschle/sslh/commit/951b708f612b9315508542b21029b07eb4e08705) - 2025-03-09

- x64
- gcc `15.0.0 20250105`

:warning: **SSE2 / AVX / AVX2** 

- Check your cpu supported instructions with [CPU-Z](https://www.cpuid.com/softwares/cpu-z.html)

  >  ![](https://github.com/nono303/PHP-memcache-dll/raw/master/avx.png)

### Dependencies

> If you have Cygwin already installed, you don't need `cygwin1.dll`, `cygpcre2-8-0.dll`, `cygev-4.dll` and `cygwrap-0.dll`
> Just ensure that you have packages `libpcre2_8_0` ,`libev4` and `libwrap0` installed and `/bin` Cygwin path is correctly set in Windows `PATH` environment variable

- **[libconfig](https://github.com/hyperrealm/libconfig/commit/690342b)** `1.7.4 dev`_(build)_
  - *cygconfig-11.dll*

- **cygwin** `3.6.0` _(cygwin)_
   - *cygwin1.dll*
- **pcre2** `10.45`_(cygwin)_
  - *cygpcre2-8-0.dll*

- **libwrap** `7.6.26`_(cygwin)_
  - *cygwrap-0.dll*

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

