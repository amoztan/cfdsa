# use MySQL ver 5.7 image
FROM mysql:5.7

# set the password
ENV MYSQL_ROOT_PASSWORD=mypassword

# copy bgg.sql to /docker-entrypoint-initdb.d directory
ADD bgg.sql /docker-entrypoint-initdb.d


