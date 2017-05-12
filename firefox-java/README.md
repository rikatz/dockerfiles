This Dockerfile (based on Jessie Frazelle [blog post](https://blog.jessfraz.com/post/docker-containers-on-the-desktop/)) main objective is to run an old, contained Firefox 51 with Java 8 plugin enabled for old sites that still uses Java Applets.

It disables Firefox Auto Update, and adds some sites needed by me in Java's exception list.

To run this container in Linux Mint 18.1, you should use the following command:

``sudo docker run -it --rm --net host -v /tmp/.X11-unix/X0:/tmp/.X11-unix -v /home/youruser/.Xauthority:/root/.Xauthority -e DISPLAY=unix$DISPLAY --name firefox rpkatz/firefox-java /firefox/firefox``

This image isn't pushed yet to Docker Hub official repo, so you should build it by the contained Dockerfile.

## TODO

* Run the image as a regular non root user
* Install WatchData token package (maybe in another image that uses this one as a base) to enable users to use their very own Token Certificate
