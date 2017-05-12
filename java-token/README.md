This image is based in the firefox-java image, and is used to open a Browser that supports the bbtoken / watchdata USB Token.


## BBToken Patch

Before you can use the wdtoken package, you must first 'patch' it to work correctly in Ubuntu newer versions, with the following procedure:

```
mkdir tmp
dpkg-deb -R wdtoken.deb tmp
sed -i 's|interruptible_sleep_on_timeout.*|msleep_interruptible (RETRY_TIMEOUT);|g' tmp/usr/src/wdtoken-1.0.0/wdtoken.c
dpkg-deb -b tmp wdtoken.deb
```
