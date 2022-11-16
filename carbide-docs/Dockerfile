# FROM node:16 as base

# RUN git clone https://github.com/rancherfederal/carbide-docs /home/node/app
# WORKDIR /home/node/app

# # remove the url path that breaks dynamic rewrites
# RUN sed -i "s/trailingSlash: false/trailingSlash: true/g" docusaurus.config.js

# # install deps
# RUN npm install

# # generate the static html
# RUN npm run build

# ###---------
# FROM cgr.dev/chainguard/nginx as deploy

# # copy over just the static html
# COPY --from=base /home/node/app/build /var/lib/nginx/html 


FROM node:16
## THIS IS JUST A STUB TO GET US INTO PRODUCTION. REDO THIS 
### BLAME BRANDON 

RUN git clone https://github.com/rancherfederal/carbide-docs /home/node/app
WORKDIR /home/node/app


RUN sed -i "s/trailingSlash: false/trailingSlash: true/g" docusaurus.config.js
#RUN sed -i 's/docusaurus serve/docusaurus serve --host 0.0.0.0/g' package.json
#RUN sed -i 's/docusaurus run/docusaurus run --host 0.0.0.0/g' package.json


RUN npm install
RUN npx docusaurus build
EXPOSE 3000

CMD [ "npm", "run", "start" ]