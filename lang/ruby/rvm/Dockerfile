FROM base

MAINTAINER Marc-Andre Cournoyer "macournoyer@gmail.com"

RUN apt-get -y update
RUN apt-get install -y -q curl

RUN curl -L https://get.rvm.io | bash -s stable --ruby
RUN /bin/bash -l -c rvm requirements

ENV PATH /usr/local/rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin