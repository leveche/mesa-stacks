FROM leveche/mesa:12778

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ="Etc/UTC"
ENV XKBLAYOUT="us"

RUN apt-get update      && \
    apt-get upgrade -y  && \
    apt-get install -y software-properties-common ca-certificates wget

RUN  wget -q https://xpra.org/gpg.asc -O /tmp/xpra-repo-key.txt

RUN  apt-key add /tmp/xpra-repo-key.txt && \
     add-apt-repository "deb https://xpra.org/ focal main"

RUN  apt-get update && \
     apt-get install -y xpra
