# hyperledger-fabric-env
Hyperledger Fabric, docker based blockchain development environment.  

```
docker-compose up
```

## Hyperledger Fabric 1.0.0-alpha2

Create work directory
```
mkdir fabric-sample
cd fabric-sample
```

Download scripts
```
curl -sSL https://goo.gl/NIKLiU | bash
```

Configure network definitions

```
crypto-config.yaml configtx.yaml
```

Generate artfacts
```
./generateArtifacts.sh <channel-ID>
```

Start environment
```
CHANNEL_NAME=<channel-ID> TIMEOUT=60 docker-compose -f docker-compose-cli.yaml up 
```

