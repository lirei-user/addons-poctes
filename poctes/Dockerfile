# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

RUN ls

# Execute during the build of the image
# ARG TEMPIO_VERSION BUILD_ARCH
# RUN \
#     curl -sSLf -o /usr/bin/tempio \
#     "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

RUN \
  apk add --no-cache \
    python3 py3-pip
RUN pip install astarte-device-sdk

# Copy root filesystem
# COPY rootfs /
# Python 3 HTTP Server serves the current working dir
# So let's set it to our add-on persistent data directory.
WORKDIR /data
# Copy data for add-on
COPY /src/ /
RUN chmod a+x /run.sh
RUN chmod a+x /client.py

CMD [ "/run.sh" ]