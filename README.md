# hyperledger-fabric-env
Hyperledger Fabric, docker based blockchain development environment.  

```
docker-compose up
```

## Hyperledger Fabric 1.0.0-alpha2

### Architecture

#### Transactions

Deploy transactions create new chaincode and take a program as parameter.

Invoke transactions perform an operation in the context of previously deployed chaincode. An invoke transaction refers to a chaincode and to one of its provided functions. 

#### State

The latest state of the blockchain (or, simply, state) is modeled as a versioned key/value store (KVS), where keys are names and values are arbitrary blobs. 

#### Ledger

Ledger provides a verifiable history of all successful state changes (we talk about valid transactions) and unsuccessful attempts to change state (we talk about invalid transactions), occurring during the operation of the system.

Ledger is constructed by the ordering service as a totally ordered hashchain of blocks of (valid or invalid) transactions.

### Nodes

**Client** or **submitting-client**: a client that submits an actual transaction-invocation to the endorsers, and broadcasts transaction-proposals to the ordering service.

**Peer**: a node that commits transactions and maintains the state and a copy of the ledger (see Sec, 1.2). Besides, peers can have a special endorser role.

**Ordering-service-node or orderer**: a node running the communication service that implements a delivery guarantee, such as atomic or total order broadcast.

#### Peer

A peer receives ordered state updates in the form of blocks from the ordering service and maintain the state and the ledger.

#### Ordering service nodes (Orderers)

Ordering service provides a shared communication channel to clients and peers, offering a broadcast service for messages containing transactions. Clients connect to the channel and may broadcast messages on the channel which are then delivered to all peers. 

### Tutorial

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

Stop environment
```
docker-compose -f docker-compose-cli.yaml down
```
or 
```
docker rm -f $(docker ps -aq)
```



