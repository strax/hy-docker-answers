FROM node:lts-alpine

EXPOSE 5000

RUN node -v && npm -v

WORKDIR /srv
COPY . /srv/
RUN npm install

CMD npm start