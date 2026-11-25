# GENERATED L-009 hermetic C build (--network=none, SBOM+SLSA-attestation-producing).
# Pinned bases; vendored source (in-tree deps) + extra build debs + runtime debs from Dockerfile.vendor.
FROM ubuntu:24.04@sha256:9c7f200c07e3d4a03e7249d2c16bf66a51120fb876aa2242cf31451412543289 AS cbuild
# dpkg-install the vendored EXTRA build debs (pkg-config/libssl-dev/...) — gcc/make are in the builder.
RUN --mount=type=bind,source=vendored/build-debs,target=/tmp/bdebs \
    set --; for f in /tmp/bdebs/*.deb; do [ -e "$f" ] && set -- "$@" "$f"; done; \
    for pass in 1 2 3 4 5; do [ $# -eq 0 ] || dpkg -i --skip-same-version "$@" >/dev/null 2>&1 && break; done; \
    dpkg --configure -a && bad= && for d in "$@"; do p=$(dpkg-deb -f "$d" Package) v=$(dpkg-deb -f "$d" Version); \
      case "$(dpkg-query -W -f='${Version} ${db:Status-Abbrev}' "$p" 2>/dev/null)" in "$v ii"*) ;; *) bad="$bad $p=$v" ;; esac; done && \
    { [ -z "$bad" ] || { echo "vendored debs not installed at their vendored version:$bad" >&2; false; }; }
WORKDIR /src
COPY vendored/nodejs-src/ .
ARG SOURCE_DATE_EPOCH=1795159451
ENV SOURCE_DATE_EPOCH=${SOURCE_DATE_EPOCH}
RUN ./configure --prefix=/opt/node
RUN make -j"$(nproc)"
RUN make install
RUN /opt/node/bin/node -v | grep -qx v26.13.1 && /opt/node/bin/node /opt/node/lib/node_modules/npm/bin/npm-cli.js -v | grep -qx 11.21.2
RUN /opt/node/bin/node -e "const c=require('crypto');if(c.createHash('sha256').update('readystack').digest('hex').length!==64)process.exit(1);if(new Intl.DateTimeFormat('de-DE',{month:'long'}).format(new Date(Date.UTC(2026,10,8)))!=='November')process.exit(1)"
FROM ubuntu:24.04@sha256:9c7f200c07e3d4a03e7249d2c16bf66a51120fb876aa2242cf31451412543289
ENV DEBIAN_FRONTEND=noninteractive PATH=/home/node/.npm-global/bin:/opt/node/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin NPM_CONFIG_PREFIX=/home/node/.npm-global LANG=C.UTF-8
RUN --mount=type=bind,source=vendored/debs,target=/tmp/debs \
    set --; for f in /tmp/debs/*.deb; do [ -e "$f" ] && set -- "$@" "$f"; done; \
    for pass in 1 2 3 4 5; do [ $# -eq 0 ] || dpkg -i --skip-same-version "$@" >/dev/null 2>&1 && break; done; \
    dpkg --configure -a && bad= && for d in "$@"; do p=$(dpkg-deb -f "$d" Package) v=$(dpkg-deb -f "$d" Version); \
      case "$(dpkg-query -W -f='${Version} ${db:Status-Abbrev}' "$p" 2>/dev/null)" in "$v ii"*) ;; *) bad="$bad $p=$v" ;; esac; done && \
    { [ -z "$bad" ] || { echo "vendored debs not installed at their vendored version:$bad" >&2; false; }; } && \
    rm -rf /var/lib/apt/lists/* \
           /var/log/dpkg.log /var/log/alternatives.log /var/log/apt /var/cache/ldconfig/aux-cache /var/cache/fontconfig
ARG SOURCE_DATE_EPOCH=1795159451
RUN groupadd -r node && useradd -r -g node -d /home/node -m node && \
    mkdir -p /home/node/.npm-global && chown -R node:node /home/node/.npm-global && \
    : "${SOURCE_DATE_EPOCH:?SOURCE_DATE_EPOCH must be set for a reproducible build}" && \
    sed -ri "s/^([^:]*:[^:]*):[0-9]*:/\1:$((SOURCE_DATE_EPOCH/86400)):/" /etc/shadow && \
    rm -f /etc/passwd- /etc/shadow- /etc/group- /etc/gshadow-
COPY --from=cbuild /opt/node /opt/node
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.title="Node.js"
LABEL org.opencontainers.image.source="https://github.com/nodejs/node"
LABEL org.opencontainers.image.description="Node.js 26.13.1 JavaScript runtime with npm, built from source, non-root"
LABEL org.opencontainers.image.version="26.13.1-CE-ubuntu24.04-r2"
LABEL org.opencontainers.image.vendor="ReadyStack.dev"
LABEL readystack.product="nodejs"
LABEL readystack.edition="CE"
LABEL readystack.build_method="source-rebuild-c"
LABEL org.opencontainers.image.revision="e9c277643b0249c50f6e6de5413be8a88ea11b6a"
# product_kind runtime: no HEALTHCHECK (a FROM base would pass it to every child image)
WORKDIR /home/node
USER node
ENTRYPOINT []
CMD ["node"]
