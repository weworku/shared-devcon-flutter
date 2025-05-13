FROM dart:stable

RUN set -x \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
        git \
        curl \
        less \
        vim \
        unzip \
        zip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENV LESSCHARSET=utf-8
ENV PATH="$PATH:/sdks/flutter/bin"
RUN set -x \
    && git clone https://github.com/flutter/flutter.git -b stable /sdks/flutter \
    && flutter upgrade \
    && useradd -m dev \
    && chown -R dev:dev /sdks/flutter/

COPY ./profile.d /etc/profile.d

WORKDIR /usr/src/app
USER dev
RUN set -x \
    && flutter --disable-analytics \
    && flutter config --enable-web --no-enable-android --no-enable-ios
