FROM ubuntu:20.04

ARG MESA_RELEASE=12778
ENV HOME=/root
ENV MESASDK_ROOT=$HOME/mesasdk
ENV MESA_DIR=$HOME/mesa


RUN apt-get update      && \
    apt-get upgrade -y

RUN  apt-get install -y curl

# SDK prereqs
RUN  apt-get install -y \
         binutils \
         make \
	     perl \
	     libx11-6 libx11-dev \
	     zlib1g zlib1g-dev  \
	     tcsh

# SDK
RUN   curl http://www.astro.wisc.edu/~townsend/resource/download/mesasdk/mesasdk-x86_64-linux-20.3.2.tar.gz | tar -C ~/ -xvz

RUN   bash -c 'echo "export MESASDK_ROOT=$MESASDK_ROOT" >> ~/.bashrc' && \
      bash -c 'echo "source ${MESASDK_ROOT}/bin/mesasdk_init.sh" >> ~/.bashrc'

# mesa download
RUN   apt-get install -y subversion
RUN   svn co -r $MESA_RELEASE https://subversion.assembla.com/svn/mesa^mesa/trunk $MESA_DIR

# mesa setup
RUN   bash -c 'echo "export MESA_DIR=$MESA_DIR" >> ~/.bashrc && \
	       echo "export OMP_NUM_THREADS=2" >> ~/.bashrc'

RUN   bash -c 'source $HOME/.bashrc && cd ${MESA_DIR} && \
	       export MESASDK_ROOT=$MESASDK_ROOT && \
	       export MESA_DIR=$MESA_DIR && \
	       source /root/mesasdk/bin/mesasdk_init.sh && \
               cd ${MESA_DIR} && ./install'
