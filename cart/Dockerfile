FROM node:14

ENV INSTANA_AUTO_PROFILE=true

EXPOSE 8080

WORKDIR /opt/server

COPY package.json package-lock.json /opt/server/
COPY node_modules /opt/server/node_modules/
COPY tracing.js /opt/server/tracing.js
COPY server.js /opt/server/

CMD ["node", "-r", "./tracing.js", "server.js"]
