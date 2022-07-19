# pull the official base image
FROM node:10-alpine
# set working direction
WORKDIR /app

RUN apk add --no-cache --virtual .gyp \
    python \
    make \
    g++ \
    && npm install \
    && apk del .gyp


# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH
# install application dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm i
# add app
COPY . ./
# start app
CMD ["npm", "start"]


