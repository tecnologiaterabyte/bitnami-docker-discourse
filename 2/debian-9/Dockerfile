FROM bitnami/minideb-extras:stretch-r311
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages advancecomp file ghostscript gifsicle hostname imagemagick jhead jpegoptim libbsd0 libc6 libcomerr2 libcurl3 libedit2 libffi6 libgcc1 libgcrypt20 libgmp-dev libgmp10 libgnutls30 libgpg-error0 libgssapi-krb5-2 libhogweed4 libicu57 libidn11 libidn2-0 libjpeg-progs libk5crypto3 libkeyutils1 libkrb5-3 libkrb5support0 libldap-2.4-2 liblzma5 libncurses5 libnettle6 libnghttp2-14 libp11-kit0 libpq5 libpsl5 libreadline7 librtmp1 libsasl2-2 libssh2-1 libssl1.0.2 libssl1.1 libstdc++6 libtasn1-6 libtinfo5 libunistring0 libxml2 libxml2-dev libxslt1-dev libxslt1.1 optipng pngcrush pngquant zlib1g zlib1g-dev
RUN bitnami-pkg install ruby-2.5.3-23 --checksum ec9f4945f80a5ef7b0f5329dc2ab214945834465c69e769b5cdf4dd7b1c2e82e
RUN bitnami-pkg unpack postgresql-client-10.7.0-1 --checksum a351a3ea00d4443bdc6892e5f9d45aaf2fbbdf7c2aa40ab6cf423c78d535cca1
RUN bitnami-pkg install git-2.21.0-0 --checksum 37eb00d863f94194c0c31464c2c747bc784e662adbab240b5f0ef46b3e259e52
RUN bitnami-pkg unpack discourse-sidekiq-2.2.2-0 --checksum f0da5b7cb6a1a132de33f40d97d929b3abff1ce576ee45a89f6985df4ce5dcfa
RUN bitnami-pkg unpack discourse-2.2.2-1 --checksum 53934aab4675054e16127080c6f69c1d631616d50285fdec91055d5d5940e370

COPY rootfs /
RUN install_packages rsync
ENV BITNAMI_APP_NAME="discourse" \
    BITNAMI_IMAGE_VERSION="2.2.2-debian-9-r12" \
    DISCOURSE_EMAIL="user@example.com" \
    DISCOURSE_EXTERNAL_PORT_NUMBER="80" \
    DISCOURSE_HOST="discourse" \
    DISCOURSE_HOSTNAME="127.0.0.1" \
    DISCOURSE_PASSWORD="bitnami123" \
    DISCOURSE_PORT="3000" \
    DISCOURSE_PORT_NUMBER="3000" \
    DISCOURSE_POSTGRESQL_NAME="bitnami_application" \
    DISCOURSE_POSTGRESQL_PASSWORD="bitnami1" \
    DISCOURSE_POSTGRESQL_USERNAME="bn_discourse" \
    DISCOURSE_SITENAME="My site!" \
    DISCOURSE_USERNAME="user" \
    PATH="/opt/bitnami/ruby/bin:/opt/bitnami/postgresql/bin:/opt/bitnami/git/bin:$PATH" \
    POSTGRESQL_CLIENT_CREATE_DATABASE_NAME="" \
    POSTGRESQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    POSTGRESQL_CLIENT_CREATE_DATABASE_USERNAME="" \
    POSTGRESQL_HOST="postgresql" \
    POSTGRESQL_PORT_NUMBER="5432" \
    POSTGRESQL_ROOT_PASSWORD="" \
    POSTGRESQL_ROOT_USER="postgres" \
    REDIS_HOST="redis" \
    REDIS_PASSWORD="" \
    REDIS_PORT_NUMBER="6379" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_TLS="true" \
    SMTP_USER=""

EXPOSE 3000

ENTRYPOINT [ "/app-entrypoint.sh" ]
CMD [ "nami", "start", "--foreground", "discourse" ]
