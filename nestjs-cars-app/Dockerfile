FROM node:14 AS production


#Dockerfile configurations settings with env files
ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

#package.json folder will copy into this direactory
WORKDIR /usr/src/api

COPY package.json .
COPY yarn.lock .

RUN yarn global add @nestjs/cli

#Installing the dev depoendencies rather than only installing only the production dependencies 
RUN yarn install --production=true

RUN apt-get -q update && apt-get -qy install netcat

COPY . .

RUN yarn build 

CMD ["sh", "-c", "yarn typeorm migration:run && yarn start:prod"]