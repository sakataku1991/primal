FROM --platform=linux/amd64 ruby:3.2.4

ARG LANG
ARG TZ

ENV ROOT=/backend
ENV LANG=${LANG}
ENV TZ=${TZ}

RUN apt-get update -qq && \
    apt-get install -y \
    bash \
    build-essential \
    default-mysql-client \
    git \
    lsof \
    tzdata \
    vim

RUN mkdir -p ${ROOT}/src
WORKDIR ${ROOT}/src

COPY src/Gemfile ./Gemfile
COPY src/Gemfile.lock ./Gemfile.lock

RUN bundle install

COPY . ${ROOT}

COPY docker/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]
