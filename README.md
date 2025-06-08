# Mining Nodes
This repository serves as a reference point to any Nodes and/or stratum bridges that I have Dockerized.

<table>
  <tr><td> Node </td> <td> Command </td> <td> Notes </td></tr>
  <tr><td>Astrix Node (AIX)</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name astrix -v /data/.astrix-node/:/root/.astrix-node theretromike/nodes:astrix</td><td></td></tr>
  <tr>
    <td> Bitcoin (BTC) </td>
    <td>docker run -d --network host --restart always --log-opt max-size=10m --name btc -v /data/.btc/:/root/.bitcoin theretromike/nodes:bitcoin</td>
    <td>If you are going to run BCH and BTC on the same system, you need to also override the P2P and RPC ports as they both use the same, like this in the /data/.btc/bitcoin.conf
      
    port=7335
    rpcport=9001
    
  </td>
  </tr>
    <tr>
    <td> Bitcoin Cash (BCH) </td>
    <td>docker run -d --network host --restart always --log-opt max-size=10m --name bch -v /data/.bch/:/root/.bitcoin theretromike/nodes:bitcoincash</td>
    <td>If you are going to run BCH and BTC on the same system, you need to also override the P2P and RPC ports as they both use the same, like this in the /data/.bch/bitcoin.conf
      
    port=6335
    rpcport=9002
    
  </td>
  <tr><td>Bonte (BONTE)</td><td>sudo docker run -d --network host --restart always --log-opt max-size=10m --name bonte -v /data/.bonte/:/root/.bontecoin theretromike/nodes:bonte</td><td></td></tr>
  </tr>
    </tr>
    <tr>
    <td> Digibyte (DGB) </td>
    <td>docker run -d --network host --restart always --log-opt max-size=10m --name dgb -v /data/.dgb/:/root/.digibyte theretromike/nodes:digibyte</td>
    <td>You must create an auto cookie (there is a python script to do it for you) and then use rpcauth instead of rpcuser and rpcpassword. You must also specify the algo the node is for, like this in the /data/.dgb/digibyte.conf
      
    rpcauth=xxx:yyy
    algo=sha256d
    
  </td>
  </tr>
  <tr><td>GoByte (GBX)</td><td>sudo docker run -d --network host --restart always --log-opt max-size=10m --name gbx -v /data/.gbx/:/root/.gobytecore theretromike/nodes:gobyte</td><td></td></tr>
  <tr><td>Griffion (GRIFF)</td><td>sudo docker run -d --network host --restart always --log-opt max-size=10m --name griff -v /data/.griff/:/root/.griffion theretromike/nodes:griffion</td><td></td></tr>
  <tr><td>Innova (INN)</td><td>sudo docker run -d --network host --restart always --log-opt max-size=10m --name inn -v /data/.inn/:/root/.innova theretromike/nodes:innova</td><td></td></tr>
  <tr><td>Pigeoncoin (PGN)</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name pgn -v /data/.pgn/:/root/.pigeoncore theretromike/nodes:pigeoncoin</td><td></td></tr>
  <tr><td>PrivacyCoin (PRCY)</td><td>docker run -d --restart always --network host --log-opt max-size=10m --name prcy -v /data/.prcy/:/root/.prcycoin theretromike/nodes:prcy</td><td></td></tr>
  <tr><td>Verus (VRSC)</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name verus -v /data/.vrsc/:/root/.komodo/VRSC theretromike/nodes:verus</td><td></td></tr>
  <tr><td>ZeroOne (ZOC)</td><td>docker run -d --restart always --network host --log-opt max-size=10m --name zoc -v /data/.zoc/:/root/.zeroonecore -v /data/.zoc_sentinel:/zoc_sentinel theretromike/nodes:zoc</td><td></td></tr>
</table>

<table>
  <tr><td> Stratum Bridge </td> <td> Command </td> <td> Notes </td></tr>
  <tr><td>Astrix Stratum Bridge</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name astrixstratum theretromike/stratums:astrix --stratum=:5001 --prom=:2001</td><td></td></tr>
</table>    

<table>
  <tr><td> Pool Component </td> <td> Command </td> <td> Notes </td></tr>
  <tr><td>Postgres</td><td>docker run -d --name postgres --restart always --log-opt max-size=10m -p 5432:5432 -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=P@ssw0rd -e POSTGRES_DB=master -v /data/.postgres/data:/var/lib/postgresql/data postgres</td><td></td></tr>
  <tr><td>PGAdmin</td><td>sudo docker run -d --name pgadmin --restart always --log-opt max-size=10m -p 81:80 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=P@ssw0rd dpage/pgadmin4</td><td>Navigate to: http://192.168.1.45:81/ (replace IP with your IP) and login with admin@admin.com and P@ssw0rd. Right click Servers, Register -> Server. Enter a name, IP, and credentials and click save. Create login for miningcore and grant login rights. Create database for miningcore and make miningcore login the db owner</td></tr>
  <tr><td>Miningcore</td><td>docker run -d --name miningcore --restart always --log-opt max-size=10m --network host -v /data/.miningcore/config.json:/app/config.json -v /data/.miningcore/coins.json:/app/build/coins.json theretromike/miningcore</td><td></td></tr>
  <tr><td>Miningcore Web UI</td><td>sudo docker run -d -p 80:8080 --name miningcore-webui --restart always --log-opt max-size=10m -e API_BASE_URL=http://192.168.1.100:4000/api -e STRATUM_HOST=192.168.1.100 -e POOL_NAME="Self-Hosted Mining Pool" theretromike/miningcorewebui</td><td>Replace IP with your IP</td></tr>
  <tr><td>Watchtower</td><td>docker run -d --name watchtower --restart always --log-opt max-size=10m -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower</td><td></td></tr>
  <tr><td>Dozzle</td><td>docker run --name dozzle -d --restart always --log-opt max-size=10m -v /var/run/docker.sock:/var/run/docker.sock -p 82:8080 amir20/dozzle:latest</td><td></td></tr>
      <tr>
    <td> Setup </td>
    <td>
      
    sudo apt update -y
    sudo fallocate -l 16G /swapfile
    sudo chmod 600 /swapfile
    sudo mkswap /swapfile
    sudo swapon /swapfile
    echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
    sudo apt install docker.io -y
    sudo mkdir /data
    sudo mkdir /data/.postgres
    sudo mkdir /data/.postgres/data
    sudo mkdir /data/.miningcore
    cd /data/.miningcore/
    wget https://raw.githubusercontent.com/TheRetroMike/rmt-miningcore/refs/heads/dev/src/Miningcore/coins.json
    sudo nano config.json
    
    ---------------
    {
        "logging": {
            "level": "info",
            "enableConsoleLog": true,
            "enableConsoleColors": true,
            "logFile": "",
            "apiLogFile": "",
            "logBaseDirectory": "",
            "perPoolLogFile": true
        },
        "banning": {
            "manager": "Integrated",
            "banOnJunkReceive": true,
            "banOnInvalidShares": false
        },
        "notifications": {
            "enabled": false,
            "email": {
                "host": "smtp.example.com",
                "port": 587,
                "user": "user",
                "password": "password",
                "fromAddress": "info@yourpool.org",
                "fromName": "support"
            },
            "admin": {
                "enabled": false,
                "emailAddress": "user@example.com",
                "notifyBlockFound": true
            }
        },
        "persistence": {
            "postgres": {
                "host": "127.0.0.1",
                "port": 5432,
                "user": "miningcore",
                "password": "miningcore",
                "database": "miningcore"
            }
        },
        "paymentProcessing": {
            "enabled": true,
            "interval": 600,
            "shareRecoveryFile": "recovered-shares.txt",
            "coinbaseString": "Mined by Retro Mike Tech"
        },
        "api": {
            "enabled": true,
            "listenAddress": "*",
            "port": 4000,
            "metricsIpWhitelist": [],
            "rateLimiting": {
                "disabled": true,
                "rules": [
                    {
                        "Endpoint": "*",
                        "Period": "1s",
                        "Limit": 5
                    }
                ],
                "ipWhitelist": [
                    ""
                ]
            }
        },
        "pools": [
      ]
    }
    ---------------
  </td>
  <td>&nbsp;</td>
  </tr>
</table>    
