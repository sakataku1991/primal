FROM --platform=linux/amd64 ruby:3.2.4

ARG WORKDIR
ARG LANG
ARG TZ

ENV ROOT=/${WORKDIR}
ENV LANG=/${LANG}
ENV TZ=/${TZ}

RUN apt-get update -qq && \
    apt-get install -y \
    bash \
    build-essential \
    default-mysql-client \
    git \
    lsof \
    tzdata \
    vim

WORKDIR ${ROOT}

COPY src/Gemfile ${ROOT}/Gemfile
COPY src/Gemfile.lock ${ROOT}/Gemfile.lock

RUN bundle install

COPY src ${ROOT}

COPY docker/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]
