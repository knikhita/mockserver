#
# MockServer Dockerfile
#
# https://github.com/jamesdbloom/mockserver
# http://www.mock-server.com
#

# pull base image
FROM openjdk:alpine

# maintainer details
MAINTAINER James Bloom "jamesdbloom@gmail.com"

# obtain MockServer jar and script
RUN apk add --update openssl ca-certificates bash wget
ADD run_mockserver.sh /opt/mockserver/run_mockserver.sh
ARG VERSION=5.3.0
ARG RESPOSITORY_URL=https://oss.sonatype.org/content/repositories/releases/org/mock-server/mockserver-netty/$VERSION/mockserver-netty-$VERSION-jar-with-dependencies.jar
RUN echo "using mockserver version $RESPOSITORY_URL"
RUN wget --max-redirect=1 -O /opt/mockserver/mockserver-netty-jar-with-dependencies.jar $RESPOSITORY_URL

# set working directory
WORKDIR /opt/mockserver

# expose ports.
EXPOSE 1080 1090

# define default command.
CMD ["/opt/mockserver/run_mockserver.sh", "-logLevel", "INFO", "-serverPort", "1080"]
