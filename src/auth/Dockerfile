FROM python:3.10-slim-bullseye

RUN sed --in-place 's/httpredir.debian.org/mirror.sov.uk.goscomb.net/' /etc/apt/sources.list \
  && apt-get update \
  && apt-get install -y --no-install-recommends --no-install-suggests \
  build-essential default-libmysqlclient-dev \
  && pip install --no-cache-dir --upgrade pip

WORKDIR /app
COPY ./requirements.txt /app
RUN pip install --no-cache-dir --requirement /app/requirements.txt
COPY . /app

EXPOSE 5000

CMD ["python3", "server.py"]