FROM python:3-slim as stage1

RUN apt update && apt install -y gcc && \
    pip install netease-dl

FROM python:3-slim

LABEL description="docker for netease-dl(https://github.com/ziwenxie/netease-dl)"

COPY --from=stage1 /usr/local/lib/python3.7/site-packages /usr/local/lib/python3.7/site-packages
COPY --from=stage1 /usr/local/bin/netease-dl /usr/local/bin/netease-dl

VOLUME [ "/output" ]

ENTRYPOINT [ "netease-dl","-o","/output" ]

CMD ["--help"]
