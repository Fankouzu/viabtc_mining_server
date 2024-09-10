## build
```sh
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
```

## run
```
矿池服务器的试运行，相关修改记录如下

1.modify config.json

jobmaster 目录下的config.json:
    "flag": "debug" //日志级别为debug
    "main_coin": {
        "name": "FB",
        "host": "38.60.171.236",
        "port": 8332,
        "user": "fractalbitcoin",
        "pass": "fractalbitcoin_1234567"
    },
    //"aux_coin":       //删除
    //rsk_job_interval  //删除
    //rsk_coin          //删除
    //vcash_coin        //删除
    "main_coin_recipient": "1FtiSHFDTpLvurxnBsSTLNT3B4aqyRxm9x",
    "coin_recipients": [
    ],
    "pool_name": "FBPool",
    "coinbase_message": "FB/BTC",


gateway 目录下的config.json:
    "flag": "debug" //日志级别为debug
    "diff_max": 1048576,

metawriter 目录下的config.json:
    "flag": "debug" //日志级别为debug

2.
mkdir -p /var/log/pool/jobmaster
mkdir -p /var/log/pool/gateway
mkdir -p /var/log/pool/metawriter

3.
cd ../jobmaster
nohup ./jobmaster.exe config.json

cd ../gateway
nohup ./gateway.exe config.json

cd ../metawriter
nohup ./metawriter.exe config.json
```
