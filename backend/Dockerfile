FROM ruby:3.0.0-alpine3.13

ENV LANG C.UTF-8
ENV TZ Asia/Tokyo

RUN apk update && \
    apk upgrade && \
    apk add --no-cache linux-headers libxml2-dev make gcc g++ libc-dev tzdata nodejs postgresql-dev postgresql yarn && \
    apk add --virtual build-packages --no-cache build-base curl-dev

RUN mkdir /app
WORKDIR /app
COPY Gemfile /app/Gemfile
COPY Gemfile.lock /app/Gemfile.lock
RUN bundle install
RUN apk del build-packages
COPY . /app


COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000
