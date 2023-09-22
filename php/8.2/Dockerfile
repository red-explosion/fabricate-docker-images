FROM docker.io/node:18-alpine AS node
FROM docker.io/composer:2.6

LABEL maintainer="Red Explosion"

WORKDIR /fabricate

COPY --from=node /usr/lib /usr/lib
COPY --from=node /usr/local/lib /usr/local/lib
COPY --from=node /usr/local/include /usr/local/include
COPY --from=node /usr/local/bin /usr/local/bin

# RUN npm install -g yarn --force
# RUN npm install -g bun

RUN npm config set cache /fabricate/.npm --global

COPY docker-entrypoint /usr/local/bin/docker-entrypoint
RUN chmod +x /usr/local/bin/docker-entrypoint

ENTRYPOINT ["docker-entrypoint"]
