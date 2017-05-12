This image is based in the firefox-java image, and is used to open a Browser that supports the bbtoken / watchdata USB Token.


## BBToken Patch

Before you can use the wdtoken package, you must first 'patch' it to work correctly in Ubuntu newer versions, with the following procedure:

```
mkdir tmp
dpkg-deb -R wdtoken.deb tmp
sed -i 's|interruptible_sleep_on_timeout.*|msleep_interruptible (RETRY_TIMEOUT);|g' tmp/usr/src/wdtoken-1.0.0/wdtoken.c
dpkg-deb -b tmp wdtoken.deb
```

## Running the Container

To run this Container (and enable Token Access), use the following command:

 ``sudo docker run  -it --rm --net host --device=/dev/WDUsbKey0 -v $HOME/.Xauthority:/root/.Xauthority -e DISPLAY=unix$DISPLAY --name firefox rpkatz/java-token /firefox/firefox``
 
 
 ## Enabling Module in firefox:
 
 * Go to Preferences / Advanced
 * Open the 'Certificates' tab
 * Open the 'Security Devices' Dialog
 * Load a new module, with the following options:
 **  Name: ICP
 ** File Name: /usr/lib/watchdata/ICP/lib/libwdpkcs_icp.so
 * Close this dialog, and then check if the Token was loaded

 
 ## TODO
 
 * Make this run as a regular user
 * Auto configure the PKCS11 module in Firefox
