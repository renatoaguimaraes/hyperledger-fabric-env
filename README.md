# hyperledger-fabric-env
Hyperledger Fabric, docker based blockchain development environment.  

```
docker-compose up
```

## Hyperledger Fabric 1.0.0-alpha2
```
mkdir fabric-sample
cd fabric-sample
./generateArtifacts.sh <channel-ID>
CHANNEL_NAME=<channel-ID> TIMEOUT=60 docker-compose -f docker-compose-cli.yaml up 
curl -sSL https://goo.gl/NIKLiU | bash
```
