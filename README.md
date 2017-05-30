# hyperledger-fabric-env
Hyperledger Fabric, docker based blockchain development environment.  

```
docker-compose up
```
- 4 peers 
- 1 orderer
- 2 ca

```
mkdir fabric-sample
cd fabric-sample
./bin/cryptogen generate --config=./crypto-config.yaml
FABRIC_CFG_PATH=$PWD
./bin/configtxgen -profile TwoOrgsOrdererGenesis -outputBlock ./channel-artifacts/genesis.block
./bin/configtxgen -profile TwoOrgsChannel -outputCreateChannelTx ./channel-artifacts/channel.tx -channelID <channel-ID>
./bin/configtxgen -profile TwoOrgsChannel -outputAnchorPeersUpdate ./channel-artifacts/Org1MSPanchors.tx -channelID <channel-ID> -asOrg Org1MSP
./bin/configtxgen -profile TwoOrgsChannel -outputAnchorPeersUpdate ./channel-artifacts/Org2MSPanchors.tx -channelID <channel-ID> -asOrg Org2MSP
./generateArtifacts.sh <channel-ID>
```

Start the network

docker-compose-cli.yaml
```
working_dir: /opt/gopath/src/github.com/hyperledger/fabric/peer
# command: /bin/bash -c './scripts/script.sh ${CHANNEL_NAME}; sleep $TIMEOUT'
volumes
```
