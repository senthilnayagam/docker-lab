# Erlang R16B HiPE with Rebar
#
# VERSION               0.0.1

FROM      base
MAINTAINER Son Tran-Nguyen "sntran@inhuman.io"

RUN apt-get update
RUN apt-get install -y git build-essential libncurses5-dev openssl libssl-dev curl
# For HiPE, requires M4
RUN apt-get install -y m4
 
RUN mkdir -p /opt/erlang/
RUN curl -O https://raw.github.com/spawngrid/kerl/master/kerl && chmod a+x kerl
RUN mv kerl /opt/erlang/
RUN ln -s /opt/erlang/kerl /usr/local/bin/kerl
 
RUN kerl update releases
RUN KERL_CONFIGURE_OPTIONS=--enable-hipe kerl build R16B R16B
RUN kerl install R16B /opt/erlang/R16B
RUN ln -s /opt/erlang/R16B /opt/erlang/current
 
RUN cd /usr/local/bin && find /opt/erlang/current/bin -exec ln -s '{}' \;
 
## Install Rebar
RUN cd /opt/erlang && git clone git://github.com/rebar/rebar.git
RUN cd /opt/erlang/rebar && ./bootstrap
RUN ln -s /opt/erlang/rebar/rebar /usr/local/bin/rebar