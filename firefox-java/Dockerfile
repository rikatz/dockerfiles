FROM ubuntu:14.04
MAINTAINER ricardo.katz@gmail.com

RUN apt-get -y update && apt-get -y dist-upgrade && apt-get -y install software-properties-common apt-utils wget bzip2 libgtk-3-bin libasound2 libxt6 libx11-xcb1 libgtk2.0-bin x11-apps

RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && echo debconf shared/accepted-oracle-license-v1-1 seen true | /usr/bin/debconf-set-selections

RUN add-apt-repository -y ppa:webupd8team/java && apt-get -y update && apt-get -y install oracle-java8-installer oracle-java8-unlimited-jce-policy

RUN wget https://ftp.mozilla.org/pub/firefox/releases/51.0/linux-x86_64/pt-BR/firefox-51.0.tar.bz2 -O - | tar -xj

RUN mkdir -p /root/.java/deployment/security && echo "http://www.serpro.gov.br\nhttps://www.serpro.gov.br" > /root/.java/deployment/security/exception.sites

RUN echo "//\npref(\"app.update.enabled\", false);\npref(\"app.update.auto\", false);" > /firefox/mozilla.cfg && echo "pref(\"general.config.obscure_value\", 0);\npref(\"general.config.filename\", \"mozilla.cfg\");" > /firefox/defaults/pref/local-settings.js
