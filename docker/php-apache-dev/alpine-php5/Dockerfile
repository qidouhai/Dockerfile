#+++++++++++++++++++++++++++++++++++++++
# Dockerfile for webdevops/php-apache-dev:alpine-php5
#    -- automatically generated  --
#+++++++++++++++++++++++++++++++++++++++

FROM webdevops/php-apache:alpine-php5

ENV WEB_DOCUMENT_ROOT=/app \
    WEB_DOCUMENT_INDEX=index.php \
    WEB_ALIAS_DOMAIN=*.vm
ENV WEB_PHP_SOCKET=127.0.0.1:9000
ENV WEB_NO_CACHE_PATTERN="\.(css|js|gif|png|jpg|svg|json|xml)$"

COPY conf/ /opt/docker/

# Install development environment
RUN /usr/local/bin/apk-install \
        # Install tools
        graphviz \
        # Install php development stuff
        php5-xdebug \
        # Tools
        nano \
        vim \
    # Enable php development services
    && docker-service-enable syslog ssh postfix \
    && /opt/docker/bin/bootstrap.sh \
    && docker-image-cleanup
