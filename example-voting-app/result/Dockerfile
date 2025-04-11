FROM node:18-slim

# add curl for healthcheck
RUN apt-get update && \
    apt-get install -y --no-install-recommends curl tini && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /usr/local/app
RUN npm install -g nodemon

COPY package*.json ./

RUN npm ci && \
 npm cache clean --force && \
 mv /usr/local/app/node_modules /node_modules

COPY . .

ENV PORT=4000
EXPOSE 4000
RUN chown -R node:node /usr/local/app
USER node
ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["node", "server.js"]
