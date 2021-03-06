FROM mhart/alpine-node:7

ARG BUILD_DATE
ARG VCS_REF

LABEL org.label-schema.build-date=$BUILD_DATE \
  org.label-schema.vcs-ref=$VCS_REF \
  org.label-schema.schema-version="1.0" \
  org.label-schema.name="skilld-zen" \
  org.label-schema.description="Skilld latest Drupal 8 zen theme image - Alpine: node, npm, gulp, kss, bower, susy & libsass" \
  org.label-schema.vcs-url="https://github.com/skilld-labs/docker-frontend" \
  maintainer="Andy Postnikov <andypost@ya.ru>"

ENV NPM_PACKAGES "bower \
  breakpoint-sass \
  browser-sync \
  chroma-sass \
  del \
  eslint \
  event-stream \
  gulp \
  gulp-autoprefixer \
  gulp-cached \
  gulp-eslint \
  gulp-if \
  gulp-load-plugins \
  gulp-rename \
  gulp-replace \
  gulp-sass \
  gulp-sass-lint \
  gulp-size \
  gulp-sourcemaps \
  gulp.spritesmith \
  kss \
  node-sass-import-once \
  glob \
  sass-lint \
  support-for \
  typey \
  zen-grids"

RUN set -e \
  && apk add --no-cache git \
  && npm install -g \
    susy@2 \
    $NPM_PACKAGES \
  && rm -rf /root/.npm /root/.config /tmp/npm*

VOLUME /work
WORKDIR /work

COPY docker-entrypoint.sh /usr/bin/
ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["gulp"]
