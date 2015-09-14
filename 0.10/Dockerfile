# VERSION 0.10.0b1
# AUTHOR:         Nicolas Lamirault <nicolas.lamirault@gmail.com>
# DESCRIPTION:    portefaix/grafana

FROM portefaix/base:3.2
MAINTAINER Nicolas Lamirault <nicolas.lamirault@gmail.com>

ENV HEKA_VERSION v0.10.0b1
ENV GOPATH /go

RUN apk add --update build-base curl go git mercurial ca-certificates cmake perl

RUN mkdir -p ${GOPATH}/src/github.com/mozilla-services/ && \
    cd ${GOPATH}/src/github.com/mozilla-services/ && \
    git clone https://github.com/mozilla-services/heka.git -b ${HEKA_VERSION} && \
    cd ${GOPATH}/src/github.com/mozilla-services/heka && \
    source build.sh && \
    mkdir /usr/share/heka && \
    cp -r /go/src/github.com/mozilla-services/heka/build/heka/* /usr/share/heka/ && \
    go clean -i -r && \
    apk del --purge build-base go git mercurial cmake perl && \
    rm -rf ${GOPATH} /tmp/* /var/cache/apk/* /root/.n*

ADD ./config.toml /usr/share/heka/config.toml

RUN for i in decoders encoders filters modules; do \
		mkdir -p /usr/share/heka/lua_${i} && \
	cp /go/src/github.com/mozilla-services/heka/sandbox/lua/${i}/* /usr/share/heka/lua_${i}; \
	done && \
	cp /go/src/github.com/mozilla-services/heka/sandbox/lua/modules/* /usr/share/heka/lua_modules && \
	cp -r /go/src/github.com/mozilla-services/heka/dasher /usr/share/heka/

EXPOSE 4881
EXPOSE 4352

CMD ["/usr/share/heka/bin/hekad", "--config", "/usr/share/heka/config.toml"]

