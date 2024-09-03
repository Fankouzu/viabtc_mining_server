
sudo apt install -y libcurl4-openssl-dev libssl-dev libpsl-dev libnghttp2-dev libsodium-dev redis-server cmake zlib1g-dev libkrb5-dev libidn2-0-dev librtmp-dev libbrotli-dev libssh-dev 

cd viabtc_mining_server/
cd depends/hiredis/
make
sudo make install
sudo ldconfig
cd ../network/
make
cd ../utils
make
cd ../jobmaster
make
cd ../blockmaster
make
cd ../bitpeer
make
cd ../gateway
make
cd ../mineragent
make
cd ../poolbench
vim makefile 
LIBS = ... -lgssapi_krb5 -lldap -llber -lidn2 -lrtmp -lbrotlidec -lssh -lpsl -lnghttp2
make
cd ../metawriter
make
cd ../metarelay
make
cd ../alertcenter
make
