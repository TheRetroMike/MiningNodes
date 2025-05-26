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
