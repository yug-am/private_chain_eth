
# Account Creation

To create accounts, use the following commands:

- Node1: `geth account new --datadir node1`
- Node2: `geth account new --datadir node2`


The passwords should be stired in each directory in `password.txt`.


The Ethereum addresses for each node are:

- Node1: `0x8caBe9A4c205b999a2D0e247F691838325604827`
- Node2: `0xD2018f7395eaB68cc400c1C01cA95332D9a53F00`

## Create Genesis.json

To create the Genesis.json file with initial allocation and two signers (Node1 & Node2), follow the provided instructions.

## Initialize Geth DB

Use the following commands to initialize the Geth DB for each node:

- Node1: `geth init --datadir node1 genesis.json`
- Node2: `geth init --datadir node2 genesis.json`

## Bootnode Key Creation

To create the Bootnode key, run the following command:

`bootnode -genkey boot.key`

## Bootnode Generation from Key

To generate the Bootnode from the key, use the following command:

`bootnode -nodekey boot.key -addr  192.168.4.142:30305`

The Enode URL will be displayed.
```
enode://<enode>
```
## Starting Nodes

Follow the provided commands to start the nodes:

### Miners

Node1:

Miners:
Node1:
```geth --datadir node1 --port 30306 --bootnodes enode://<enode> --networkid 141319 --unlock  0x8caBe9A4c205b999a2D0e247F691838325604827 --password node1/password.txt  --mine --miner.etherbase 0x8caBe9A4c205b999a2D0e247F691838325604827 --http --http.addr '0.0.0.0' --allow-insecure-unlock --syncmode full --ipcpath geth-node1.ipc --miner.gasprice 0```

Node2:
```geth --datadir node2 --port 30307 --bootnodes enode://<enode> --networkid 141319 --unlock  0xD2018f7395eaB68cc400c1C01cA95332D9a53F00 --password node2/password.txt  --mine --miner.etherbase 0xD2018f7395eaB68cc400c1C01cA95332D9a53F00  --http --http.port 8546 --authrpc.port 8547 --http.addr '0.0.0.0' --allow-insecure-unlock --syncmode full --ipcpath geth-node2.ipc --miner.gasprice 0 ```


Non miner nodes:




Node2:
```geth --datadir node2 --port 30310 --bootnodes enode://<enode> --networkid 141319 --unlock  0xD2018f7395eaB68cc400c1C01cA95332D9a53F00 --password node2/password.txt  --http --http.port 8550 --authrpc.port 8551 --http.addr '0.0.0.0' --allow-insecure-unlock --syncmode full --ipcpath geth-node2.ipc```

---
Initial Balances:
| Address                                   | Balance   |
| ----------------------------------------- | --------- |
| E94B2fc61C602cfd5F25ae2bcD1205e1136982cF | 900,000,000 |
| 20d4214e1614e0608BE8eF4B9e12a9A3ca4a0833 | 800,000,000 |

---

## Attach to Nodes

To attach to each node, use the following commands:

Windows:
- Node1: `geth attach ipc:\\\\.\\pipe\\geth-node1.ipc`
  
- Node2: `geth attach ipc:\\\\.\\pipe\\geth-node2.ipc`

Ubunto:

- Node1: `geth attach node1/geth-node1.ipc`

- Node2: `geth attach node2/geth-node2.ipc`

---

## Balance Check

To check the balance of each node, use the following commands:
current Node:

`eth.getBalance(eth.accounts[0])`

You can also check the balance of the current account with `eth.getBalance(eth.accounts[0])`

---

## Send Transaction

To send a transaction to each node, use the following commands:

Send transaction:
To Node1 :

```eth.sendTransaction({from: eth.accounts[0], to: '0x8caBe9A4c205b999a2D0e247F691838325604827', value: 3700, gasPrice: 0 })```

To Node2 :

```eth.sendTransaction({from: eth.accounts[0], to: '0xD2018f7395eaB68cc400c1C01cA95332D9a53F00', value: 3700, gasPrice: 0 })```




## Propose Miner
View signers:
```clique.getSigners()```

Approve
- Making Node2 signer
```clique.propose("0xD2018f7395eaB68cc400c1C01cA95332D9a53F00", true)```




##### Pending :
```txpool.status```

```txpool.content```



###### Transaction 1





```eth.getTransaction('0x738cc7c476e3da3d7c5ca27ce434bad3855256f457b40b81a96689b9b52f8ab8')```

```
{
  blockHash: "0x0bcae4a1bf43eb5b4e3b85e5bb897dc4af2a89293a8532876376c3e70eb5ad5d",
  blockNumber: 13,
  chainId: "0x3039",
  from: "0xD2018f7395eaB68cc400c1C01cA95332D9a53F00",
  gas: 21000,
  gasPrice: 0,
  hash: "0x738cc7c476e3da3d7c5ca27ce434bad3855256f457b40b81a96689b9b52f8ab8",
  input: "0x",
  nonce: 0,
  r: "0xebc76a4de000a6c06e91e9549d16c09225bb3bdd22a8c00f53b20bee0cf4cea8",
  s: "0x42ccde8b3e930f8266be5265644a9f3d1f725810902917a8f4ff08ab0b1d2a2f",
  to: "0x8caBe9A4c205b999a2D0e247F691838325604827",
  transactionIndex: 0,
  type: "0x0",
  v: "0x6095",
  value: 3700
}

```





## Genesis.json
```
{
  "config": {
    "chainId": 12345,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "berlinBlock": 0,
    "clique": {
      "period": 30,
      "epoch": 30000
    }
  },
  "difficulty": "1",
  "gasLimit": "8000000",
  "extradata": "0x0000000000000000000000000000000000000000000000000000000000000000E94B2fc61C602cfd5F25ae2bcD1205e1136982cF20d4214e1614e0608BE8eF4B9e12a9A3ca4a0833000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "alloc": {
    "E94B2fc61C602cfd5F25ae2bcD1205e1136982cF": { "balance": "900000000" },
    "20d4214e1614e0608BE8eF4B9e12a9A3ca4a0833": { "balance": "800000000" }
  }
}

```

