FROM python:3.10-slim-bullseye

RUN apt-get update && apt-get install -y --no-install-recommends --no-install-suggests \
    -o Acquire::Retries=5 \
    -o Acquire::http::Timeout=120 \
    -o Acquire::https::Timeout=120 \
    build-essential libpq-dev python3-dev && pip install --no-cache-dir --upgrade pip

WORKDIR /app
COPY ./requirements.txt /app

RUN pip install --no-cache-dir --requirement /app/requirements.txt
COPY . /app

EXPOSE 5000

CMD ["python", "server.py"]