FROM alpine:latest

ENV RELEASE_URL https://github.com/winterssy/music-get/releases/download/v1.7.0/music-get_1.7.0_linux_x86_64.tar.gz

LABEL description="dockerized music-get(https://github.com/winterssy/music-get)"
LABEL dockerfile_author="https://github.com/othorizon"

VOLUME [ "/data/downloads" ]

WORKDIR /data
RUN wget ${RELEASE_URL} && tar -xf music-get_1.7.0_linux_x86_64.tar.gz -C . && echo success

CMD [ "sh" ]