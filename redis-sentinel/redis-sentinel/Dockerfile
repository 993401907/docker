FROM daocloud.io/library/redis

ADD ./redis-sentinel/sentinel.conf /etc/redis/sentinel.conf
RUN chown redis:redis /etc/redis/sentinel.conf

ENV SENTINEL_QUORUM 2
ENV SENTINEL_DOWN_AFTER 30000
ENV SENTINEL_FAILOVER 180000
COPY ./redis-sentinel/docker-entrypoint.sh /usr/local/bin/
COPY ./redis-sentinel/sentinel-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh
RUN chmod +x /usr/local/bin/sentinel-entrypoint.sh
ENTRYPOINT ["sentinel-entrypoint.sh"]

# https://blog.csdn.net/miaodichiyou/article/details/88951618