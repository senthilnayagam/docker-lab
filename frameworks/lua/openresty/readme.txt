docker run -i -t ubuntu /bin/bash

apt-get install -y libreadline-dev libncurses5-dev libpcre3-dev libssl-dev perl make nano wget

cd /tmp
wget http://openresty.org/download/ngx_openresty-1.4.1.3.tar.gz

tar xzvf ngx_openresty-1.4.1.3.tar.gz

cd ngx_openresty-1.4.1.3
./configure --with-luajit
make
make install

docker commit 99682ac26f10 senthilnayagam/openresty

7a00e4707ab1

docker push senthilnayagam/openresty