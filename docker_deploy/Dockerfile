#make sure host name at db_param.h file is mydb instead of localhost
FROM  --platform=linux/amd64 ubuntu:20.04
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install --assume-yes apt-utils
RUN apt-get -y update && apt-get -y install gcc g++ make git wget autoconf libtool automake python pkg-config
RUN apt-get -y install postgresql build-essential libpq-dev libpqxx-dev


EXPOSE 1234
EXPOSE 2345

# install google protocol buffer
RUN wget https://github.com/google/protobuf/releases/download/v3.6.0/protobuf-cpp-3.6.0.tar.gz
RUN tar xzf protobuf-cpp-3.6.0.tar.gz
RUN cd ./protobuf-3.6.0  && ./configure && make && make install
RUN ldconfig

RUN cd ..

ADD . /worldsim
RUN chmod +x /worldsim/wait-for-it.sh
RUN chmod +x /worldsim/server
WORKDIR /worldsim
