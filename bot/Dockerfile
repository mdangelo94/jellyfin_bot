FROM python:3.11-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    ffmpeg \
    build-essential \
    libxml2-dev \
    libxslt1-dev \
    git \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

WORKDIR /app

RUN git clone https://github.com/Arrowar/StreamingCommunity.git .

RUN pip install --no-cache-dir -r requirements.txt

# Entrypoint esterno (lo monti tu da host)
ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]