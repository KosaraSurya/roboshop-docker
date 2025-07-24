# # creating image and having size in GBs
# FROM node:20
# WORKDIR /opt/server/
# COPY package.json /opt/server/
# COPY *.js /opt/server/
# RUN npm install
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node","server.js"]

# # Minimizing image now the size will be in MBs
# FROM node:20-alpine3.21
# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# WORKDIR /opt/server/
# COPY package.json /opt/server/
# COPY *.js /opt/server/
# RUN npm install
# RUN chown -R roboshop:roboshop /opt/server
# ENV MONGO="true"\
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# USER roboshop
# CMD ["node","server.js"]


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
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
USER roboshop
# Here we are copying build-1 output into build-2 directory
COPY --from=builder /opt/server /opt/server 
CMD ["node","server.js"]