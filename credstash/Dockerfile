FROM alpine:latest as build


RUN apk --update add \
    python \
    gcc \
    g++ \
    openssl \
    openssl-dev \
    python-dev \
    libffi-dev \
    openssl-dev \
    linux-headers \
    curl

RUN curl https://bootstrap.pypa.io/get-pip.py > get-pip.py && \
    python get-pip.py

RUN pip install credstash

FROM alpine:latest as runtime

RUN apk --update add python openssl libffi
COPY --from=build /usr/lib/python2.7/site-packages /usr/lib/python2.7/site-packages
COPY --from=build /usr/bin/credstash /usr/bin/credstash

CMD ["credstash"]
