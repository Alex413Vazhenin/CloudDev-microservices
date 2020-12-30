## Build from Ionic container to reduce build time
FROM beevelop/ionic AS ionic
# App directory creation
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
# Using npm ci, because it's faster
RUN npm install
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html