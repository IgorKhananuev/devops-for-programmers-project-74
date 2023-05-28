FROM node:20.1.0-slim

RUN echo "deb http://security.debian.org/debian-security bullseye-security main contrib non-free" > /etc/apt/sources.list
RUN apt-get update


WORKDIR /app
RUN chmod 755 /app

COPY package.json .
COPY package-lock.json .

RUN npm install --force

COPY . .

CMD ["bash", "-c", "npm run migrate && npx fastify start -a 0.0.0.0 -l info -P app.js"]
