FROM node:current-alpine as base

RUN apk add git hugo

RUN git clone https://github.com/kubernetes/website.git /home/node/app
WORKDIR /home/node/app
RUN git submodule update --init --recursive --depth 1

# install deps
RUN npm install
# generate static HTML
RUN hugo

###---------
FROM cgr.dev/chainguard/nginx as deploy

# copy over just the static html
COPY --from=base /home/node/app/public /var/lib/nginx/html 
# /usr/share/nginx/html/
