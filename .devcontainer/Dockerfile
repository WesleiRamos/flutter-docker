FROM instrumentisto/flutter:latest

# Instala o socat para permitir conexão do flutter com o dispositivo
RUN apt-get update && apt-get -y install socat

WORKDIR /home/developer

EXPOSE 6111

# Checa se o flutter está instalado corretamente
RUN flutter doctor
