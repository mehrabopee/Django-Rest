FROM python:3.10

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

RUN apt-get update && \
    apt-get install -y netcat-openbsd gettext && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir /code
COPY . /code/
WORKDIR /code

RUN set -e; \
    /usr/local/bin/python -m pip install --upgrade pip ;\
    python -m pip install -r /code/requirements.txt ;\
    chmod +x /code/docker/entrypoints/entrypoint.sh ;

EXPOSE 8000
ENTRYPOINT ["/code/docker/entrypoints/entrypoint.sh"]


