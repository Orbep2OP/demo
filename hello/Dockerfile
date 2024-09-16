#Usually start from an base image in this case the image is an OS that contains the Go compiler and language environment
FROM golang:1.17-alpine AS build

WORKDIR /src/
COPY main.go go.* /src/
RUN CGO_ENABLED=0 go build -o /bin/demo

# Scratch is the minimal image needed to run Go binaries (which are also self-contained)
FROM scratch 
COPY --from=build /bin/demo /bin/demo
ENTRYPOINT ["/bin/demo"]