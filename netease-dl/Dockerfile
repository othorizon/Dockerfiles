FROM alpine/git:1.0.7 as stage1

ENV NETEASE_DL_GIT https://github.com/ziwenxie/netease-dl
RUN git clone $NETEASE_DL_GIT /netease_dl_git

FROM python:3.6 as stage2

COPY --from=stage1 /netease_dl_git /netease_dl_git
WORKDIR /netease_dl_git
RUN python setup.py install

FROM python:3.6-alpine

LABEL description="dockerized netease-dl(https://github.com/ziwenxie/netease-dl)"
LABEL dockerfile_author="https://github.com/othorizon"

COPY --from=stage2 /usr/local/lib/python3.6/site-packages /usr/local/lib/python3.6/site-packages
COPY --from=stage2 /usr/local/bin/netease-dl /usr/local/bin/netease-dl

VOLUME [ "/output" ]

ENTRYPOINT [ "netease-dl","-o","/output" ]

CMD ["--help"]
