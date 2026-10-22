# The image goreleaser publishes to ghcr.io/katbyte/ipmi_exporter on a release tag: the build context holds the prebuilt program per platform,
# so this only adds FreeIPMI and copies it onto alpine. upstream's Dockerfile expects promu's .build/ output instead, so it is left as it is.
# Like upstream's image it carries FreeIPMI's tools, which the exporter runs unless started with --native-ipmi, and runs as nobody.
# alpine comes from Google's mirror of Docker Hub, which does not turn a shared release runner away for having pulled too much.
FROM mirror.gcr.io/library/alpine:3.24
RUN apk add --no-cache freeipmi
ARG TARGETPLATFORM
COPY $TARGETPLATFORM/ipmi_exporter /bin/ipmi_exporter
EXPOSE 9290
USER nobody
ENTRYPOINT ["/bin/ipmi_exporter"]
