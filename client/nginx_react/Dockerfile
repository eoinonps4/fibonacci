FROM node:16-alpine as builder

USER node
# create this dir vbefore specifcying workdir to avoid 
# permissions conflict, if dir wasnt there it would be created with root ownership
RUN mkdir -p /home/node/app
WORKDIR 'home/node/app'

# chown sets ownership of copied files, think of chmod
COPY --chown=node:node ./package.json ./
RUN npm install
COPY --chown=node:node ./ ./
RUN npm run build

FROM nginx as nginx_server
EXPOSE 3000
# Bring in nginx server set up
COPY ./nginx_react/default.conf /etc/nginx/conf.d/default.conf
# Copy prod assets created in last step
COPY --from=builder /home/node/app/build /usr/share/nginx/html