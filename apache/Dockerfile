FROM httpd:2.4-alpine

RUN sed -i "s/#LoadModule\ rewrite_module/LoadModule\ rewrite_module/" /usr/local/apache2/conf/httpd.conf;

COPY dev.conf /usr/local/apache2/conf/dev.conf

RUN echo "Include /usr/local/apache2/conf/dev.conf" \
    >> /usr/local/apache2/conf/httpd.conf

RUN mkdir -p /usr/local/apache2/vhosts

RUN echo "Include /usr/local/apache2/vhosts/*.conf" \
    >> /usr/local/apache2/conf/httpd.conf

