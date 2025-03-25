FROM python:3.11-slim-bullseye

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt install -y git gcc g++ make python3-dev python3-pip python3-venv libxml2-dev libxslt1-dev zlib1g-dev gettext curl redis-server pkg-config && \
    curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs && \
    apt-get install -y mariadb-server libmariadb-dev && \
    apt-get auto-remove -y && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /

COPY repo/requirements.txt .
COPY repo/additional_requirements.txt .

RUN pip3 install -r requirements.txt && \
    pip3 install -r additional_requirements.txt

RUN rm -rf requirements.txt additional_requirements.txt
RUN pip install setuptools
RUN pip install legacy-cgi
RUN npm install -g sass postcss-cli postcss autoprefixer
