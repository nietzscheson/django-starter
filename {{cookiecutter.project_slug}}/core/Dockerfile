FROM python:3.9 AS base

ENV PYTHONUNBUFFERED 1

RUN pip3 install --upgrade pipenv
RUN apt-get update && apt-get install -y --no-install-recommends gcc

COPY Pipfile* ./

RUN pipenv lock
RUN pipenv install --system --deploy

RUN useradd --create-home core
WORKDIR /home/core
USER core

COPY . ./

