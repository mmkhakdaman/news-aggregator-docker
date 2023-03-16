FROM node:16-alpine  AS builder

RUN apk --update --no-cache add git

# Set working directory
WORKDIR /app

RUN ls -l
# git clone project
RUN git clone https://github.com/mmkhakdaman/news-aggregator-frontend.git .

# yarn install
RUN yarn && yarn build

FROM nginx:alpine AS serve

WORKDIR /var/www/html


COPY --from=builder /app/dist/  .
