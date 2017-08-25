FROM amazonlinux:2017.03
LABEL maintainer="maehachi08"

ENV DIND_COMMIT="3b5fac462d21ca164b3778647420016315289034"
COPY dockerd-entrypoint.sh /usr/local/bin/

RUN set -x && \

    yum install -y \
      docker \
      aws-cli \
      vim-enhanced \
      git \
      wget && \

    wget -O /usr/local/bin/dind "https://raw.githubusercontent.com/docker/docker/${DIND_COMMIT}/hack/dind" && \
    chmod +x /usr/local/bin/dind && \
    chmod +x /usr/local/bin/dockerd-entrypoint.sh && \

    yum clean all

VOLUME /var/lib/docker
EXPOSE 2375

ENTRYPOINT ["/usr/local/bin/dockerd-entrypoint.sh"]
