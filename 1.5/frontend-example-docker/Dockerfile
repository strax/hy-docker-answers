FROM node:lts-alpine

EXPOSE 5000

ENV API_URL=http://localhost:8000

RUN node -v && npm -v

WORKDIR /srv
COPY . /srv/
RUN npm install

CMD npm start