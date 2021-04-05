FROM ubuntu:groovy

RUN apt update -qq \
  && apt install -y -qq \
    jq \
    apt-transport-https \
    ca-certificates \
    curl \
    apt-utils \
    software-properties-common \
    dnsutils \
  && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - \
  && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu groovy stable" \
  && apt update -qq \
  && apt install -y -qq \
    docker-ce \
  && apt  -qq clean \
  && apt autoremove -y \
  && rm -rf \
    /var/lib/apt/lists/* \
    /tmp/* \
    /var/tmp/*

COPY auto-scale.sh /auto-scale.sh
RUN chmod a+x /auto-scale.sh

CMD ["/auto-scale.sh"]
