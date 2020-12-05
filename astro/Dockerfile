FROM leveche/mesa-xpra:12778
ENV HOME=/root

RUN apt-get update      && \
    apt-get upgrade -y  && \
    apt-get install -y emacs vim nano-tiny

RUN apt-get install -y python3-matplotlib python3-numpy

RUN apt-get install -y ssh


RUN rm /etc/update-motd.d/* && \
    echo "**** MESA worker node ****" > /etc/motd

RUN apt-get install -y xarclock

RUN echo 'export DISPLAY=:0' >> $HOME/.bashrc

ENTRYPOINT service ssh restart && \
           xpra start :0 --bind-tcp=0.0.0.0:10000 --start=xarclock && \
           sleep 31536000
