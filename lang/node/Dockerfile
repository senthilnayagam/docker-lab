FROM base
RUN apt-get update -qq
RUN apt-get install -q -y software-properties-common
RUN add-apt-repository -y ppa:chris-lea/node.js
RUN apt-get update -qq
RUN apt-get install -q -y nodejs



# DOCKER-VERSION 0.5.2

FROM   base

MAINTAINER davejlong

RUN apt-get -y install git-core

# Install Node.js
ENV NODE_ROOT /opt/node

RUN apt-get -y install python g++ make
RUN mkdir /node
RUN cd /node
RUN git clone -b v0.10.15 git://github.com/joyent/node.git src
RUN cd /node/src
RUN ls -lahGA ./
RUN ./configure --prefix=$NODE_ROOT
RUN make
RUN make install

ENV PATH "$NODE_ROOT/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Install RVM
RUN apt-get -y install curl
RUN curl -L https://get.rvm.io | bash -s stable --ruby
RUN source /usr/local/rvm/scripts/rvm

# Use Ruby 2.0.0
RUN rvm use 2.0.0 --default
RUN bundle install

ADD . /src

EXPOSE 5000
CMD ["bundle", "exec", "foreman", "start"]
