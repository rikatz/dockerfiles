FROM rpkatz/firefox-java

COPY ./wdtokentool-icp_1.1.0-3_all.deb /root

RUN apt-get -y install dkms gcc make libnss3 linux-headers-$(uname -r) && dpkg -i /root/wdtokentool-icp_1.1.0-3_all.deb && apt-get clean all

