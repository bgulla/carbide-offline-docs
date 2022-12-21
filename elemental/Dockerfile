
FROM node:16 as base
## THIS IS JUST A STUB TO GET US INTO PRODUCTION. REDO THIS 
### BLAME BRANDON 

RUN git clone https://github.com/rancher/elemental-docs /home/node/app
WORKDIR /home/node/app


#RUN sed -i "s/trailingSlash: false/trailingSlash: true/g" docusaurus.config.js
#RUN sed -i 's/docusaurus serve/docusaurus serve --host 0.0.0.0/g' package.json
#RUN sed -i 's/docusaurus run/docusaurus run --host 0.0.0.0/g' package.json


RUN npm install
RUN npm run build
###---------
FROM cgr.dev/chainguard/nginx as deploy

# copy over just the static html
COPY --from=base /home/node/app/build /var/lib/nginx/html 