FROM eclipse-temurin:21

ENV ANDROID_HOME /android_sdk
ENV BUILD_TOOLS_VER 35.0.0-rc1
ENV PLATFORM_VER 34
ENV BUILD_TOOLS_VER 35.0.0-rc1

WORKDIR /android_sdk

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
		unzip \
        git \
    && apt-get upgrade -y \
	&& rm -rf /var/lib/apt/lists/*

RUN curl https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip -o sdk.zip \
    && unzip sdk.zip \
    && rm sdk.zip \
    && cd cmdline-tools \
    && mkdir latest \
    && mv lib bin NOTICE.txt source.properties latest

RUN yes | $ANDROID_HOME/cmdline-tools/latest/bin/sdkmanager --licenses || true

RUN cmdline-tools/latest/bin/sdkmanager \
    "build-tools;$BUILD_TOOLS_VER" \
    "platforms;android-$PLATFORM_VER" \
    "sources;android-$PLATFORM_VER" \
    "build-tools;$BUILD_TOOLS_VER" \
    "platform-tools"

WORKDIR /app
