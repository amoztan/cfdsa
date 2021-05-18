# the base image
FROM node:16


# define some env variables
ENV APP_ROOT=/app APP_PORT=3000 
ENV BGG_DB_HOST=dockerlocalhost BGG_DB_PORT=3306 BGG_DB_USER=root BGG_DB_PASSWORD=changeit

# create the /app and cd into /app
WORKDIR ${APP_ROOT}

# inside APP_ROOT
# copy the following files
ADD main.js .
ADD package.json .
ADD package-lock.json .
# copt these directories
ADD bootstrap_public bootstrap_public
ADD bootstrap_views bootstrap_views
ADD lib lib
ADD public public
ADD views views

# install the packages in package.json
RUN npm i

## running the image
# add healthcheck
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
	CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1
# document that this container listens on port 3000
EXPOSE ${APP_PORT}

# run the application
ENTRYPOINT ["node", "main.js","--html"]

