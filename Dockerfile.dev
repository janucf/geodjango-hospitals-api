FROM python:3.11-slim-buster

WORKDIR /app

LABEL maintainer="JCF WEB-GIS"
LABEL description="Imagem de desenvolvimento para a API em GeoDjango 'Hospitals' "

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN <<EOF
    set -xe
    apt-get update
    apt-get -y install \
        binutils \
        gcc \
        gdal-bin \
        libproj-dev \
        netcat \
        postgresql \
        python-gdal \
        python3-gdal
    apt-get clean
EOF

COPY --link requirements.txt /app/

RUN --mount=type=cache,id=pip,target=/root/.cache,sharing=locked \
    <<EOF
    set -xe
    python3 -m pip install -U pip
    python3 -m pip install -Ur requirements.txt
EOF

COPY . /app