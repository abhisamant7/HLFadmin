kubectl exec -it fabric-tools -- /bin/bash
export CHANNEL_NAME="dfarmchannel"
cd /fabric
configtxgen -profile dfarmchannel -outputCreateChannelTx ${CHANNEL_NAME}.tx -channelID ${CHANNEL_NAME}

export ORDERER_URL="orderer0.dfarmadmin-service:7050"
export CORE_PEER_ADDRESSAUTODETECT="false"
export CORE_PEER_NETWORKID="nid1"
export CORE_PEER_LOCALMSPID="dfarmadmin"
export CORE_PEER_MSPCONFIGPATH="/fabric/crypto-config/peerOrganizations/dfarmadmin/peers/peer0.dfarmadmin/msp/"
export FABRIC_CFG_PATH="/etc/hyperledger/fabric"
peer channel create -o ${ORDERER_URL} -c ${CHANNEL_NAME} -f /fabric/${CHANNEL_NAME}.tx 
exit

kubectl exec -it fabric-tools -- /bin/bash
cp /fabric/config/configtx.yaml /fabric/
cd /fabric
configtxgen -profile OrdererGenesis -outputBlock genesis.block
exit



kubectl exec -it fabric-tools - /bin/bash
cp /fabric/config/configtx.yaml /fabric/
cd /fabric
configtxgen -profile OrdererGenesis -outputBlock genesis.block
exit

kubectl exec -it fabric-tools - /bin/bash
cd /fabric
configtxgen -profile dfarmchannel -outputAnchorPeersUpdate ./dfarmadminanchors.tx -channelID dfamchannel -asOrg dfarmadmin
configtxgen -profile dfarmchannel -outputAnchorPeersUpdate ./dfarmretailanchors.tx -channelID dfarmchannel -asOrg dfarmretail


10.100.139.141   dfarmadmin-ca
10.100.116.191   dfarmretail-ca  
10.100.41.30     orderer0-service 
10.100.61.252    orderer1-service 
10.100.119.10    orderer2-service
10.100.167.102   peer0-dfarmadmin 
10.100.108.171   peer0-dfarmretail
10.100.46.178    peer1-dfarmadmin  
10.100.160.60    peer1-dfarmretail  


sg-003fd1fc22361deb4
sg-03768bf40a1c6750f
sg-0c40fd6627038277b

eks-remoteAccess-a2b7a0de-e7e7-7e76-b5e5-99d3be707a46, eks-cluster-sg-DfarmBlockchain-763657106. view inbound rules. view outbound rules


sg-03768bf40a1c6750f
sg-081d222a107097b7a
sg-0c40fd6627038277b
sg-07390e553cfd70d3f

===========================================

kubectl exec -it fabric-tools - /bin/bash
cp /fabric/config/configtx.yaml /fabric/
cd /fabric
configtxgen -profile OrgsOrdererGenesis -outputBlock genesis.block
exit


NAME                 TYPE           CLUSTER-IP       EXTERNAL-IP                                                              PORT(S)                          AGE
dfarmadmin-ca        LoadBalancer   10.100.156.152   a4a3bedc836d311ea9fec02845472515-167887471.us-east-2.elb.amazonaws.com   30054:30770/TCP,7054:32603/TCP   52m
dfarmretail-ca       LoadBalancer   10.100.38.54     a58c6366136d311ea9fec02845472515-474758205.us-east-2.elb.amazonaws.com   30054:31976/TCP,7054:31548/TCP   51m
kubernetes               10.100.0.1       <none>                                                                   443/TCP                          22d
orderer1                 10.100.140.230   <none>                                                                   7050/TCP                         40m
orderer2                 10.100.50.42     <none>                                                                   7050/TCP                         40m
orderer3                 10.100.155.122   <none>                                                                   7050/TCP                         40m
peer0-dfarmadmin         10.100.45.246    <none>                                                                   7051/TCP,7061/TCP,5984/TCP       6s
peer0-dfarmaretail       10.100.112.225   <none>                                                                   7051/TCP,7061/TCP,5984/TCP       8m12s
peer1-dfarmadmin         10.100.87.147    <none>                                                                   7051/TCP,7061/TCP,5984/TCP       10m
peer1-dfarmaretail       10.100.183.221   <none>                                                                   7051/TCP,7061/TCP,5984/TCP       7m4

10.100.0.10:53  orderer0-service
10.100.170.113   orderer1-service
10.100.141.22    orderer2-service
10.100.60.88     peer0-dfarmadmin-service
10.100.168.12    peer1-dfarmadmin-service
10.100.212.195   peer0-dfarmretail-service
10.100.243.245    peer1-dfarmretail-service
10.100.177.138   dfarmadmin-ca 
10.100.118.183   dfarmretail-ca 


CORE_PEER_MSPCONFIGPATH=/fabric/crypto-config/peerOrganizations/dfarmadmin/users/Admin@dfarmadmin/msp

CORE_PEER_LOCALMSPID="dfarmadmin"
CORE_PEER_ADDRESS=peer0-dfarmadmin:7051
CORE_PEER_TLS_ROOTCERT_FILE=/fabric/crypto-config/peerOrganizations/dfarmadmin/peers/peer0.dfarmadmin/tls/ca.crt

export CHANNEL_NAME=dfarmchannel

peer channel create -o orderer0-service:7050 -c dfarmchannel -f /fabric/dfarmchannel.tx --tls --cafile /fabric/crypto-config/ordererOrganizations/default.svc.cluster.local/orderers/orderer0.default.svc.cluster.local/tls/ca.crt



kubectl exec -it peer0-dfarmadmin-deployment-775698dccd-4mmvp -- /bin/bash
cd /etc
apt-get update
apt-get install vim -y
vi hosts

kubectl logs -f orderer2-deployment-9bc9b7dff-8twc9


=================================

cd /fabric
configtxgen -profile OrdererGenesis -outputBlock genesis.block
exit


kubectl exec -it fabric-tools -- /bin/bash
cd /fabric
configtxgen -profile dfarmchannel -outputAnchorPeersUpdate ./dfarmadminanchors.tx -channelID dfarmchannel -asOrg dfarmadmin
configtxgen -profile dfarmchannel -outputAnchorPeersUpdate ./dfarmretailanchors.tx -channelID dfarmchannel -asOrg dfarmretail


kubectl exec -it fabric-tools -- /bin/bash
cp /fabric/config/configtx.yaml /fabric/
cd /fabric
configtxgen -profile OrdererGenesis -outputBlock genesis.block
exit


cp /crypto-config/peerOrganizations/dfarmadmin/ca/55ed91305f5f9d167beed7bc8753faa351f754ae284331e8c49085746ca5e0c9_sk /fabric/msp/keystore
============================================================================


cd /fabric
configtxgen -profile OrdererGenesis -outputBlock genesis.block
exit


../bin/cryptogen generate --config=./crypto-config.yaml
export FABRIC_CFG_PATH=$PWD
mkdir channel-artifacts
../bin/configtxgen -profile dfarmMultiNodeEtcdRaft -outputBlock ./channel-artifacts/genesis.block
../bin/configtxgen -profile dfarmchannel -outputCreateChannelTx ./channel-artifacts/channel.tx -channelID mychannel
../bin/configtxgen -profile TwoOrgsChannel -outputAnchorPeersUpdate ./channel-artifacts/dfarmadminMSPanchors.tx -channelID mychannel -asOrg dfarmadminMSP
../bin/configtxgen -profile TwoOrgsChannel -outputAnchorPeersUpdate ./channel-artifacts/Org2MSPanchors.tx -channelID mychannel -asOrg Org2MSP


kubectl exec -it fabric-tools -- /bin/bash
cd /fabric
configtxgen -profile dfarmchannel -outputAnchorPeersUpdate ./dfarmadminanchors.tx -channelID dfarmchannel -asOrg dfarmadmin
configtxgen -profile dfarmchannel -outputAnchorPeersUpdate ./dfarmretailanchors.tx -channelID dfarmchannel -asOrg dfarmretail

configtxgen -profile dfarmchannel -outputCreateChannelTx ./dfarmchannel.tx -channelID dfarmchannel 

kubectl exec -it fabric-tools -- /bin/bash
export CHANNEL_NAME="dfarmchannel"
cd /fabric
configtxgen -profile dfarmchannel -outputCreateChannelTx ${CHANNEL_NAME}.tx -channelID ${CHANNEL_NAME}

export ORDERER_URL="orderer0-service:7050"
export CORE_PEER_ADDRESSAUTODETECT="false"
export CORE_PEER_LOCALMSPID="dfarmadmin"
export CORE_PEER_MSPCONFIGPATH="/fabric/crypto-config/peerOrganizations/dfarmadmin/peers/peer0.dfarmadmin/msp/"
export FABRIC_CFG_PATH="/etc/hyperledger/fabric"
peer channel create -o ${ORDERER_URL} -c ${CHANNEL_NAME} -f /fabric/${CHANNEL_NAME}.tx 
exit





10.100.139.141   dfarmadmin-ca
10.100.116.191   dfarmretail-ca  
10.100.41.30     orderer0-service 
10.100.61.252    orderer1-service 
10.100.119.10    orderer2-service
10.100.167.102   peer0-dfarmadmin 
10.100.108.171   peer0-dfarmretail
10.100.46.178    peer1-dfarmadmin  
10.100.160.60    peer1-dfarmretail  

192.168.166.91  dfarmadmin-ca-86745599cc-m25x4
192.168.199.24  dfarmretail-ca-7559cfc8b7-dc5tw
192.168.144.206 orderer0-deployment-8544f9bd64-lnw7f
192.168.215.165 orderer1-deployment-78c556596-hrslf
192.168.172.47  orderer2-deployment-7d8cbbd76-q99ct
192.168.245.216 peer0-dfarmadmin-deployment-596fb5f554-cwc5n
192.168.206.172 peer0-dfarmretail-deployment-7cf699d7c6-2jk9q
192.168.129.13  peer1-dfarmadmin-deployment-649747745d-97qwq
192.168.168.142 peer1-dfarmretail-deployment-776c5f7fc8-g6ptw

kubectl exec -it peer1-dfarmretail-deployment-776c5f7fc8-g6ptw  -- /bin/bash
cd /etc
vi hosts


CORE_PEER_MSPCONFIGPATH=/fabric//crypto-config/peerOrganizations/dfarmadmin.com/users/Admin@dfarmadmin.com/msp

CORE_PEER_LOCALMSPID="dfarmadminMSP"

CORE_PEER_ADDRESS=peer0.dfarmadmin.com:7051

CORE_PEER_TLS_ROOTCERT_FILE=/fabric/crypto-config/peerOrganizations/dfarmadmin.com/peers/peer0.dfarmadmin.com/tls/ca.crt

export CHANNEL_NAME=dfarmchannel


peer channel create -o orderer:7050 -c $CHANNEL_NAME -f /fabric/channel.tx  --tls --cafile /fabric/crypto-config/ordererOrganizations/dfarmadmin.com/orderers/orderer.dfarmadmin.com/msp/tlscacerts/tlsca.dfarmadmin.com-cert.pem


configtxgen -profile MainChannel -outputCreateChannelTx dfarmchannel.tx -channelID dfarmchannel

kubectl exec -it fabric-tools -- /bin/bash
export CHANNEL_NAME="dfarmchannel"
cd /fabric
configtxgen -profile OrdererGenesis -outputCreateChannelTx ${CHANNEL_NAME}.tx -channelID ${CHANNEL_NAME}

export CHANNEL_NAME="dfarmchannel"
export ORDERER_URL="orderer0-service:7050"
export CORE_PEER_ADDRESSAUTODETECT="false"
export CORE_PEER_NETWORKID="nid1"
export CORE_PEER_LOCALMSPID="dfarmadmin"
export CORE_PEER_MSPCONFIGPATH="/fabric/crypto-config/peerOrganizations/dfarmadmin/peers/peer0.dfarmadmin/msp/"
export FABRIC_CFG_PATH="/etc/hyperledger/fabric"
peer channel create -o ${ORDERER_URL} -c ${CHANNEL_NAME} -f /fabric/${CHANNEL_NAME}.tx 
exit



configtxgen -profile OrdererGenesis -outputBlock genesis.block -channelID dfarmchannel
../bin/configtxgen -profile Channel -outputCreateChannelTx ./channel-artifacts/channel.tx -channelID mychannel
../bin/configtxgen -profile Channel -outputAnchorPeersUpdate ./channel-artifacts/Org1MSPanchors.tx -channelID mychannel -asOrg Org1MSP
../bin/configtxgen -profile Channel -outputAnchorPeersUpdate ./channel-artifacts/Org2MSPanchors.tx -channelID mychannel -asOrg Org2MSP



kubectl exec -it fabric-tools -- /bin/bash
cp /fabric/config/configtx.yaml /fabric/
cd /fabric
configtxgen -profile OrdererGenesis -outputBlock genesis.block
exit