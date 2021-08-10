오류수정
sudo apt-get install python

커머셜페이퍼
cd ~/fabric-samples/commercial-paper/organization/magnetocorp/configuration/cli/
./monitordocker.sh net_basic
docker-compose -f docker-compose.yml up -d cliMagnetoCorp
cd ~/fabric-samples/commercial-paper/organization/magnetocorp/contract/
docker exec cliMagnetoCorp peer chaincode install -n papercontract -v 0 -p /opt/gopath/src/github.com/contract -l node
docker exec cliMagnetoCorp peer chaincode instantiate -n papercontract -v 0 -l node -c ‘{“Args”:[“org.papernet.commercialpaper:instantiate”]}’ -C mychannel -P “AND (‘Org1MSP.member’)”

cd ~/fabric-samples/commercial-paper/organization/magnetocorp/application/
npm install
node addToWallet.js
node issue.js

cd ~/fabric-samples/commercial-paper/organization/digibank/configuration/cli/
docker-compose -f docker-compose.yml up -d cliDigiBank

cd ~/fabric-samples/commercial-paper/organization/digibank/application/
npm install
node addToWallet.js
node buy.js
node redeem.js
