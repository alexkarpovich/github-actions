FROM python:3.9-slim

ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1

WORKDIR /app

RUN apt-get update \
  && apt-get install gcc libpq-dev python3-dev \
  --no-install-recommends -y

RUN python -m venv .venv \
  && . .venv/bin/activate \
  && pip install --upgrade pip \
  && pip install poetry

COPY pyproject.toml poetry.lock ./

RUN . .venv/bin/activate \
  && poetry config virtualenvs.create false \
  && poetry install --no-root --no-dev

