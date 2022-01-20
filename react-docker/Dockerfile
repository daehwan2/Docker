FROM node:17-alpine3.14
WORKDIR /react-docker

ENV PATH="./node_modules/.bin:$PATH"
COPY . .
RUN npm run build
CMD ["npm","start"]