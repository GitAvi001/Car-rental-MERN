FROM node:14 as production 

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}


WORKDIR /usr/src/app

COPY package.json .
COPY yarn.lock .


RUN yarn install --production=false

COPY . . 

RUN yarn build

#executing the server.js file according to the node command
CMD ["node", "server.js"]