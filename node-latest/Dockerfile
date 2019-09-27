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

RUN yarn global add ember-cli