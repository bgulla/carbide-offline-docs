FROM node:16 as base

RUN git clone https://github.com/rancher/rancher-docs /home/node/app
WORKDIR /home/node/app

# remove the url path that breaks dynamic rewrites
#RUN sed -i "s/rke2-docs\///g" docusaurus.config.js

# install deps
RUN npm install

# generate the static html
RUN npm run build

###---------
FROM cgr.dev/chainguard/nginx as deploy

# copy over just the static html
COPY --from=base /home/node/app/build /var/lib/nginx/html 
