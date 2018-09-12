ARG RUBY_IMAGE

FROM $RUBY_IMAGE

RUN apt-get update && apt-get install sudo

ARG IM_VERSION

ENV IM_VERSION=${IM_VERSION}

COPY install /tmp/install

RUN bash /tmp/install/imagemagick.sh

RUN apt-get update && apt-get install graphicsmagick -y

RUN useradd --create-home --user-group --uid 1000 app && \
  mkdir /app /vendor && \
  chown -R app /app /vendor

ENV LANG=C.UTF-8 \
  LC_ALL=C.UTF-8 \
  BUNDLE_JOBS=4 \
  BUNDLE_PATH=/vendor/bundle

USER app

WORKDIR /app
