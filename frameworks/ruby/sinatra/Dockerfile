# DOCKER-VERSION 0.5.3
FROM ubuntu:12.10
RUN apt-get update
RUN apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion pkg-config wget -y
RUN wget ftp://ftp.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p247.tar.gz
RUN tar xvf ruby-2.0.0-p247.tar.gz
RUN cd ruby-2.0.0-p247; ./configure; make install
RUN gem update --system
RUN gem install bundler
ADD . /src
RUN cd /src; bundle install
EXPOSE 4567
CMD ["ruby", "/src/app.rb"]