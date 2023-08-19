# FROM docker/whalesay:latest
# LABEL Name=nextjs Version=0.0.1
# RUN apt-get -y update && apt-get install -y fortunes
# CMD ["sh", "-c", "/usr/games/fortune -a | cowsay"]

FROM node:lts as builder

WORKDIR /app

# ENV NODE_OPTIONS=--openssl-legacy-provider

COPY . .

RUN yarn install --non-interactive

RUN yarn build

# RUN rm -rf node_modules && \
#   NODE_ENV=production yarn install \
#   --prefer-offline \
#   --pure-lockfile \
#   --non-interactive \
#   --production=true

FROM node:lts

WORKDIR /app

COPY --from=builder /app  .

ENV HOST 0.0.0.0
EXPOSE 3000

CMD [ "yarn", "start" ]