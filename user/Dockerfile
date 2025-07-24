# # Here we are creating images and its size will be in GBs
# FROM node:20
# WORKDIR /opt/server/
# COPY package.json /opt/server/
# COPY *.js /opt/server/
# RUN npm install
# ENV MONGO="true"\
#     REDIS_URL="redis://redis:6379"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node","server.js"]


# Here we are doing optimiing layes(multilayer concept)
FROM node:20
WORKDIR /opt/server/
ENV MONGO="true"\
    REDIS_URL="redis://redis:6379"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"

COPY package.json /opt/server/
COPY *.js /opt/server/
RUN npm install
CMD ["node","server.js"]