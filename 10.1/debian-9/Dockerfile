FROM bitnami/minideb-extras-base:stretch-r342
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/" \
    OS_ARCH="amd64" \
    OS_FLAVOUR="debian-9" \
    OS_NAME="linux"

# Install required system packages and dependencies
RUN install_packages libaio1 libaudit1 libc6 libcap-ng0 libgcc1 libjemalloc1 libncurses5 libpam0g libssl1.0.2 libstdc++6 libtinfo5 zlib1g
RUN . ./libcomponent.sh && component_unpack "mariadb" "10.1.41-2" --checksum d6b08dbce5eec4ea7b8b96824be1f8982866908c4ea71820dcd8f015c05ee345
RUN mkdir /docker-entrypoint-initdb.d

COPY rootfs /
RUN /postunpack.sh
ENV ALLOW_EMPTY_PASSWORD="no" \
    BITNAMI_APP_NAME="mariadb" \
    BITNAMI_IMAGE_VERSION="10.1.41-debian-9-r31" \
    MARIADB_DATABASE="" \
    MARIADB_MASTER_HOST="" \
    MARIADB_MASTER_PORT_NUMBER="" \
    MARIADB_MASTER_ROOT_PASSWORD="" \
    MARIADB_MASTER_ROOT_USER="" \
    MARIADB_PASSWORD="" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_REPLICATION_MODE="" \
    MARIADB_REPLICATION_PASSWORD="" \
    MARIADB_REPLICATION_USER="" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MARIADB_USER="" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/mariadb/bin:/opt/bitnami/mariadb/sbin:$PATH"

EXPOSE 3306

USER 1001
ENTRYPOINT [ "/entrypoint.sh" ]
CMD [ "/run.sh" ]
