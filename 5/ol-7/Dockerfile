FROM bitnami/oraclelinux-extras:7-r509
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/"

# Install required system packages and dependencies
RUN install_packages bzip2-libs glibc keyutils-libs krb5-libs libcom_err libffi libselinux ncurses-libs nss-softokn-freebl openssl-libs pcre readline sqlite xz-libs zlib
RUN bitnami-pkg install python-3.6.9-2 --checksum 66cd0029243b797825cf74faab4bf6030ecac6152b67646881259da1a1c321c0
RUN bitnami-pkg install elasticsearch-curator-5.8.1-0 --checksum bd068de882316817e4894557640b68478cfc2de1a480254cc5f873306519db15
RUN localedef -c -f UTF-8 -i en_US en_US.UTF-8

COPY rootfs /
ENV BITNAMI_APP_NAME="elasticsearch-curator" \
    BITNAMI_IMAGE_VERSION="5.8.1-ol-7-r1" \
    LANG="en_US.UTF-8" \
    LANGUAGE="en_US:en" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/python/bin:/opt/bitnami/elasticsearch-curator/bin:$PATH"

USER 1001
ENTRYPOINT [ "curator" ]
CMD [ "--help" ]