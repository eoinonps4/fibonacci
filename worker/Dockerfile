FROM node:14.14.0-alpine
WORKDIR '/app'
COPY ./package.json ./ 
RUN npm install --verbose
COPY . .
# npm run start is the prod version of npm run dev
# it corresponds to what we defined in package.json under "scripts"
# ie we had a dev and start option defined there
CMD ["npm","run","start"]