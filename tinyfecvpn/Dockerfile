FROM alpine:3.11 as builder

WORKDIR /

RUN apk add --no-cache git  build-base linux-headers && \
 git clone --recursive https://github.com/wangyu-/tinyfecVPN.git && \
 cd tinyfecVPN && \
 make amd64

FROM alpine:3.11
COPY --from=builder /tinyfecVPN/tinyvpn_amd64 /bin/
ENTRYPOINT [ "/bin/tinyvpn_amd64" ]