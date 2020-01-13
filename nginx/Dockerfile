FROM centos:7

RUN yum install gcc wget git pcre-devel openssl-devel make -y
# RUN apk add pcre-dev openssl-dev zlib-dev

RUN mkdir /src
WORKDIR /src

RUN curl https://nginx.org/download/nginx-1.16.1.tar.gz > nginx-1.16.1.tar.gz
RUN tar xf nginx-1.16.1.tar.gz
RUN git clone https://github.com/arut/nginx-rtmp-module.git
RUN git clone https://github.com/openresty/redis2-nginx-module.git

WORKDIR /src/nginx-1.16.1
RUN ./configure --add-module=../nginx-rtmp-module \
--add-module=../redis2-nginx-module \
--with-http_secure_link_module \
--with-pcre \
--with-mail \
--with-select_module \
--with-poll_module \
--with-http_ssl_module \
--with-http_realip_module \
--with-http_addition_module \
--with-http_sub_module \
--with-http_dav_module \
--with-http_flv_module \
--with-http_mp4_module \
--with-http_gunzip_module \
--with-http_gzip_static_module \
--with-http_auth_request_module \
--with-http_random_index_module \
--with-http_secure_link_module \
--with-http_degradation_module \
--with-http_stub_status_module \
--with-mail \
--with-mail_ssl_module \
--with-http_v2_module

RUN make
RUN make install

COPY nginx.conf /usr/local/nginx/conf/nginx.conf
RUN mkdir -p /var/www
WORKDIR /var/www

EXPOSE 80/tcp
EXPOSE 443/tcp

CMD ["/usr/local/nginx/sbin/nginx"]

# --prefix=/home/xtreamcodes/iptv_xtream_codes/nginx/
# --conf-path=/home/xtreamcodes/iptv_xtream_codes/nginx/conf/nginx.conf
# --error-log-path=/home/xtreamcodes/iptv_xtream_codes/logs/error.log
# --add-module=./nginx-rtmp-module-master
# --http-log-path=/home/xtreamcodes/iptv_xtream_codes/logs/access.log
# --pid-path=/home/xtreamcodes/iptv_xtream_codes/nginx/nginx.pid
# --with-cc-opt='-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wp,-D_FORTIFY_SOURCE=2 -static -static-libgcc'
# --lock-path=/home/xtreamcodes/iptv_xtream_codes/tmp/nginx.lock
# --http-client-body-temp-path=/home/xtreamcodes/iptv_xtream_codes/tmp/client_temp
# --http-proxy-temp-path=/home/xtreamcodes/iptv_xtream_codes/tmp/proxy_temp
# --http-fastcgi-temp-path=/home/xtreamcodes/iptv_xtream_codes/tmp/fastcgi_temp
# --http-uwsgi-temp-path=/home/xtreamcodes/iptv_xtream_codes/tmp/uwsgi_temp
# --http-scgi-temp-path=/home/xtreamcodes/iptv_xtream_codes/tmp/scgi_temp
# --with-ld-opt='-Wl,-z,relro -Wl,--as-needed -static'
# --with-cpu-opt=generic
# --with-pcre
# --with-mail
# --with-ipv6 deprecated
# --with-rtsig_module
# --with-select_module
# --with-poll_module
# --with-http_ssl_module
# --with-http_spdy_module
# --with-http_realip_module
# --with-http_addition_module
# --with-http_sub_module
# --with-http_dav_module
# --with-http_flv_module
# --with-http_mp4_module
# --with-http_gunzip_module
# --with-http_gzip_static_module
# --with-http_auth_request_module
# --with-http_random_index_module
# --with-http_secure_link_module
# --with-http_degradation_module
# --with-http_stub_status_module
# --with-mail
# --with-mail_ssl_module
# --with-openssl=./openssl-1.0.1e