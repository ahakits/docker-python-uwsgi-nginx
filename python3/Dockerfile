FROM python:3.7-alpine

RUN mkdir /var/www

WORKDIR /var/www

COPY app/requirements.txt ./
RUN apk add --no-cache --virtual=python-build-dependencies \
        gcc make musl-dev linux-headers libffi-dev openssl-dev \
        && pip install --upgrade pip \
        && pip install -r requirements.txt \
        && apk del python-build-dependencies

COPY app ./

CMD ["uwsgi", "--ini", "/var/www/uwsgi.ini"]

