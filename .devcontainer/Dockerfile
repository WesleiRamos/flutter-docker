FROM instrumentisto/flutter:latest

# Instala o socat para permitir conexão do flutter com o dispositivo
RUN apt-get update && apt-get install -y \
  socat \
  wget \
  unzip \
  && rm -rf /var/lib/apt/lists/*

# Configuração do Gradle
ENV GRADLE_VERSION=8.9
ENV GRADLE_HOME=/opt/gradle/gradle-${GRADLE_VERSION}
ENV PATH=${GRADLE_HOME}/bin:${PATH}

# Download e instalação do Gradle
RUN wget -q https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
  && mkdir -p /opt/gradle \
  && unzip -q -d /opt/gradle gradle-${GRADLE_VERSION}-bin.zip \
  && rm gradle-${GRADLE_VERSION}-bin.zip \
  && ln --symbolic "${GRADLE_HOME}/bin/gradle" /usr/bin/gradle \
  && gradle --version

# Aceita as licenças do Android SDK
RUN yes | sdkmanager --licenses

# Instala Android SDK Platform
# Android 12
RUN sdkmanager "platforms;android-31"
# Ultimo android
RUN sdkmanager "platforms;android-35"

WORKDIR /home/developer

EXPOSE 6111

# Checa se o flutter está instalado corretamente
RUN flutter doctor
