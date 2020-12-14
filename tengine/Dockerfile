FROM debian

RUN apt-get update && apt-get install -y \
	curl \
        gcc  \
        libpcre3-dev \
	libssl-dev \
 	zlib1g-dev \
	make

RUN curl https://tengine.taobao.org/download/tengine-2.3.2.tar.gz > /opt/tengine-2.3.2.tar.gz

WORKDIR /opt

RUN tar xzf tengine-2.3.2.tar.gz

WORKDIR /opt/tengine-2.3.2

RUN ./configure

RUN make

RUN make install

RUN ln -sf /stdout/dev /usr/local/nginx/logs/access.log \
    && ln -sf /dev/stderr /usr/local/nginx/logs/error.log

EXPOSE 80

RUN ["chmod", "+x", "/usr/local/nginx"]

CMD ["/usr/local/nginx", "-g", "daemon off;"]


