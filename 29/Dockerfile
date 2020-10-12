FROM adoptopenjdk:8-jdk-hotspot

ENV ANDROID_COMPILE_SDK		29
ENV ANDROID_BUILD_TOOLS		29.0.3
ENV ANDROID_SDK_TOOLS		6609375_latest

ENV GRADLE_USER_HOME	$PWD/gradle-package-cache
ENV ANDROID_HOME	$PWD/android-sdk-linux
ENV PATH		$PATH:$PWD/android-sdk-linux/platform-tools/

RUN mkdir --parents $GRADLE_USER_HOME && \
    apt-get --quiet update --yes && \
    apt-get --quiet install --yes tar unzip lib32stdc++6 lib32z1 curl && \
    rm -rf /var/lib/apt/lists/* && \
    curl --http2 -C- -sSL -o android-sdk.zip https://dl.google.com/android/repository/commandlinetools-linux-$ANDROID_SDK_TOOLS.zip && \
    echo N | unzip -d android-sdk-linux android-sdk.zip && \
    rm android-sdk.zip && \
    yes | android-sdk-linux/tools/bin/sdkmanager --sdk_root="$ANDROID_HOME" "platforms;android-$ANDROID_COMPILE_SDK" "platform-tools" "build-tools;$ANDROID_BUILD_TOOLS" && \
    yes | android-sdk-linux/tools/bin/sdkmanager --sdk_root="$ANDROID_HOME" --licenses

