FROM debian:bullseye

# Instalar Python e pip
RUN apt update && apt install -y python3 python3-pip

# Crear directorio de traballo
WORKDIR /app

# Instalar dependencias
COPY requirements.txt .

RUN pip3 install -r requirements.txt

# Comando de inicio
CMD ["python3", "app.py"]
