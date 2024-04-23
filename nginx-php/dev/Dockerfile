FROM nginx:1.25.5

RUN apt-get update && apt-get upgrade -y \
    && rm -rf /var/lib/apt/lists/*

RUN touch /var/run/nginx.pid

RUN chown 1000 /var/cache/nginx \
    /var/run/nginx.pid

USER 1000

WORKDIR /app/public

ADD default.conf /etc/nginx/conf.d/default.conf
