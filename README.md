# error-oryx-build

Repository to show the problems using oryx build with poetry and python 3.10.x with version `<=20230904.1` (as of now).

To reporduce the error please run first

```bash
export PYTHON_VERSION=3.10.8   
```

followed by

```bash
docker run \
    -e PYTHON_VERSION \
    -v "$PWD:/repo" \
    mcr.microsoft.com/oryx/build:20230904.1 \
    oryx build /repo
```

This will result in the following error `GLIBC_2.29' not found`.

The complete logs are:
```
Operation performed by Microsoft Oryx, https://github.com/Microsoft/Oryx
You can report issues at https://github.com/Microsoft/Oryx/issues

Oryx Version: 0.2.20230904.1, Commit: f2d28cc9e92250b08ae08ccedf3b64dc4944b762, ReleaseTagName: 20230904.1

Build Operation ID: 11a0f29eb881c789
Repository Commit : 0fbde53ecfaa830bd9bd8fa296223d2f29551a89
OS Type           : stretch
Image Type        : full

Detecting platforms...
Detected following platforms:
  python: 3.10.8
Version '3.10.8' of platform 'python' is not installed. Generating script to install it...


Source directory     : /repo
Destination directory: /repo


Downloading and extracting 'python' version '3.10.8' to '/tmp/oryx/platforms/python/3.10.8'...
Detected image debian flavor: stretch.
Downloaded in 13 sec(s).
Verifying checksum...
Extracting contents...
performing sha512 checksum for: python...
Done in 15 sec(s).

Python Version: /tmp/oryx/platforms/python/3.10.8/bin/python3.10
Creating directory for command manifest file if it does not exist
Removing existing manifest file
Python Virtual Environment: pythonenv3.10
Creating virtual environment...
/tmp/oryx/platforms/python/3.10.8/bin/python3.10: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.29' not found (required by /tmp/oryx/platforms/python/3.10.8/lib/libpython3.10.so.1.0)
/tmp/oryx/platforms/python/3.10.8/bin/python3.10: /lib/x86_64-linux-gnu/libpthread.so.0: version `GLIBC_2.30' not found (required by /tmp/oryx/platforms/python/3.10.8/lib/libpython3.10.so.1.0)
/tmp/oryx/platforms/python/3.10.8/bin/python3.10: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.28' not found (required by /tmp/oryx/platforms/python/3.10.8/lib/libpython3.10.so.1.0)
/tmp/oryx/platforms/python/3.10.8/bin/python3.10: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.25' not found (required by /tmp/oryx/platforms/python/3.10.8/lib/libpython3.10.so.1.0)
/tmp/oryx/platforms/python/3.10.8/bin/python3.10: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.26' not found (required by /tmp/oryx/platforms/python/3.10.8/lib/libpython3.10.so.1.0)
/tmp/oryx/platforms/python/3.10.8/bin/python3.10: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.27' not found (required by /tmp/oryx/platforms/python/3.10.8/lib/libpython3.10.so.1.0)
```