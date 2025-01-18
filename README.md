# MiningNodes
This repository will serve as a reference point to any Nodes and/or stratums that I have Dockerized. GitHub has removed my ability to fork projects and execute GitHub actions so some of these docker images may not match the latest version of the node software

| App     | Command |
| ------- | ------- |
| Astrix Node  | docker run -d --network host --restart always --log-opt max-size=10m --name astrix -v /data/astrix-node/:/root/.astrix-node theretromike/nodes:astrix |
| Astrix Stratum Bridge | docker run -d --network host --restart always --log-opt max-size=10m --name astrixstratum theretromike/stratums:astrix --stratum=:5001 --prom=:2001 |
