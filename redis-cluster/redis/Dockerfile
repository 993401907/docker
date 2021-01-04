FROM daocloud.io/library/redis

#修复时区
ENV REDIS_PORT 8000
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN echo 'Asia/Shanghai' >/etc/timezone
ADD ./redis/redis.conf /etc/redis/redis.conf
COPY ./redis/entrypoint.sh /usr/local/bin/
RUN chmod 777 /etc/redis/redis.conf
RUN chmod +x /usr/local/bin/entrypoint.sh
EXPOSE $REDIS_PORT

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
CMD ["redis-server", "/etc/redis/redis.conf"]