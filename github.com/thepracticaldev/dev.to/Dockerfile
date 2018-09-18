FROM ruby:alpine

ENV BUNDLE_JOBS=4 RAILS_LOG_TO_STDOUT=true RAILS_SERVE_STATIC_FILES=true

COPY --from=node:alpine /usr/local /usr/local
COPY --from=node:alpine /opt /opt

RUN apk update && apk add --no-cache git build-base postgresql-dev tzdata less

RUN adduser -u 1000 -D app
RUN mkdir -p /app/tmp
RUN mkdir /vendor
RUN chown -R app /app /vendor

WORKDIR /app

USER app
