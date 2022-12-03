# Build Stage
FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y cmake clang

## Add source code to the build stage.
ADD . /home/mayhem/mayhem-cmake-example
WORKDIR /home/mayhem/mayhem-cmake-example

## ADD YOUR BUILD INSTRUCTIONS HERE.
RUN mkdir build 
WORKDIR build/
RUN CC=clang CXX=clang++ cmake ..
RUN make

# Package Stage
FROM --platform=linux/amd64 ubuntu:20.04

## TODO: Change <Path in Builder Stage>
COPY --from=builder /home/mayhem/mayhem-cmake-example/build/fuzzme /
