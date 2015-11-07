from alpine

RUN apk --update add build-base ca-certificates ruby-dev \
     && rm -rf /var/cache/apk/*

RUN echo 'gem: --no-document' >> /etc/gemrc
RUN gem install fluentd
RUN gem install fluent-plugin-elasticsearch

RUN mkdir -p /fluentd
RUN mkdir -p /fluentd/etc
RUN mkdir -p /fluentd/plugins

COPY fluentd_docker_es.conf /fluentd/etc/

EXPOSE 24224

CMD exec fluentd -c /fluentd/etc/fluentd_docker_es.conf