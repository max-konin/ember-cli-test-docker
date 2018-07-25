FROM node:latest

# Install Chrome
RUN apt-get update &&\
    apt-get install -y \
        apt-transport-https \
        gnupg \
        --no-install-recommends &&\
    curl -sSL https://dl.google.com/linux/linux_signing_key.pub | apt-key add - &&\
    echo "deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google-chrome.list &&\
    apt-get update &&\
    apt-get install -y \
        google-chrome-stable --no-install-recommends

RUN sed -i 's/"$@"/--no-sandbox "$@"/g' /opt/google/chrome/google-chrome

# Install FF
ARG FIREFOX_VERSION=58.0.2
RUN apt-get update -qqy \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/* \
  && wget --no-verbose -O /tmp/firefox.tar.bz2 https://download-installer.cdn.mozilla.net/pub/firefox/releases/$FIREFOX_VERSION/linux-x86_64/en-US/firefox-$FIREFOX_VERSION.tar.bz2 \
  && rm -rf /opt/firefox \
  && tar -C /opt -xjf /tmp/firefox.tar.bz2 \
  && rm /tmp/firefox.tar.bz2 \
  && mv /opt/firefox /opt/firefox-$FIREFOX_VERSION \
  && ln -fs /opt/firefox-$FIREFOX_VERSION/firefox /usr/bin/firefox
