FROM node:20.1.0-alpine

WORKDIR /app
RUN mkdir -p node_modules 

RUN npm insrall -g npm@9.6.6 && npm install -g vite@4.3.5

CMD ["/bin/sh", "-c", "yarn install && yarn dev"]