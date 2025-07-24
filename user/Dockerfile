# Here we are using multi stage labels to reduce the images size
# Build-1(builder)
FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY package.json /opt/server
COPY *.js /opt/server/
RUN npm install


# Build-2
FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV MONGO="true"\
    REDIS_URL="redis://redis:6379"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
USER roboshop
# Here we are copying build-1 output into build-2 directory
COPY --from=builder /opt/server /opt/server 
CMD ["node","server.js"]

#------------------------------------------------------------------------------------------

# # Here we are doing optimiing layes(multilayer concept) setting up in order
# FROM node:20
# WORKDIR /opt/server/
# ENV MONGO="true"\
#     REDIS_URL="redis://redis:6379"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"

# COPY package.json /opt/server/
# COPY *.js /opt/server/
# RUN npm install
# CMD ["node","server.js"]

#--------------------------------------------------------------------------------------------

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


