from ruby:2.6.3-alpine

RUN set -ex && \
    apk add --update build-base yarn nodejs postgresql-dev tzdata && \
    apk upgrade && \
    rm -rf /var/cache/apk

ENV BUNDLE_PATH=/var/lib/ruby/gems

RUN gem install bundler

WORKDIR /srv/coral

COPY Gemfile* yarn* package*.json /srv/coral/

RUN bundle install
RUN yarn install --check-files

COPY . /srv/coral

CMD ["bin/rails", "s", "-b", "0.0.0.0"]
