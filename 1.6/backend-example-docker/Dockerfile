FROM node:lts-alpine

ENV FRONT_URL=http://localhost:5000

EXPOSE 8000

COPY . /srv
WORKDIR /srv

RUN npm install

CMD npm start