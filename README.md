# Mining Nodes
This repository serves as a reference point to any Nodes and/or stratum bridges that I have Dockerized.

<table>
  <tr><td> Node </td> <td> Command </td> <td> Notes </td></tr>
  <tr><td>Astrix Node</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name astrix -v /data/.astrix-node/:/root/.astrix-node theretromike/nodes:astrix</td><td></td></tr>
  <tr>
    <td> Bitcoin </td>
    <td>docker run -d --network host --restart always --log-opt max-size=10m --name btc -v /data/.btc/:/root/.bitcoin theretromike/nodes:bitcoin</td>
    <td>If you are going to run BCH and BTC on the same system, you need to also override the P2P and RPC ports as they both use the same, like this in the /data/.btc/bitcoin.conf
      
    port=7335
    rpcport=9001
    
  </td>
  </tr>
    <tr>
    <td> Bitcoin Cash </td>
    <td>docker run -d --network host --restart always --log-opt max-size=10m --name bch -v /data/.bch/:/root/.bitcoin theretromike/nodes:bitcoincash</td>
    <td>If you are going to run BCH and BTC on the same system, you need to also override the P2P and RPC ports as they both use the same, like this in the /data/.bch/bitcoin.conf
      
    port=6335
    rpcport=9002
    
  </td>
  </tr>
    </tr>
    <tr>
    <td> Digibyte </td>
    <td>docker run -d --network host --restart always --log-opt max-size=10m --name dgb -v /data/.dgb/:/root/.digibyte theretromike/nodes:digibyte</td>
    <td>You must create an auto cookie (there is a python script to do it for you) and then use rpcauth instead of rpcuser and rpcpassword. You must also specify the algo the node is for, like this in the /data/.dgb/digibyte.conf
      
    rpcauth=xxx:yyy
    algo=sha256d
    
  </td>
  </tr>
  <tr><td>Griffion</td><td>sudo docker run -d --network host --restart always --log-opt max-size=10m --name griff -v /data/.griff/:/root/.griffion theretromike/nodes:griffion</td><td></td></tr
  <tr><td>Pigeoncoin</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name pgn -v /data/.pgn/:/root/.pigeoncore theretromike/nodes:pigeoncoin</td><td></td></tr>
  <tr><td>Verus</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name verus -v /data/.vrsc/:/root/.komodo/VRSC theretromike/nodes:verus</td><td></td></tr>
</table>

<table>
  <tr><td> Stratum Bridge </td> <td> Command </td> <td> Notes </td></tr>
  <tr><td>Astrix Stratum Bridge</td><td>docker run -d --network host --restart always --log-opt max-size=10m --name astrixstratum theretromike/stratums:astrix --stratum=:5001 --prom=:2001</td><td></td></tr>
</table>    
