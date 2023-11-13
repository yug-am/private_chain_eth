

# Account Creation

To create accounts, use the following commands:

- Node1: `geth account new --datadir node1`
- Node2: `geth account new --datadir node2`

The passwords should be stired in each directory in `password.txt`.


The Ethereum addresses for each node are:

- Node1: `0xF3C152F925729bF10Ce2cFEA5d63268729d04a93`
- Node2: `0x0CEc2ee4c45294475cF462B0461AA8251A680Df8`

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

`bootnode -nodekey boot.key`

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
```geth --datadir node1 --port 30306 --bootnodes enode://<enode> --networkid 14641 --unlock  0xF3C152F925729bF10Ce2cFEA5d63268729d04a93 --password node1/password.txt  --mine --miner.threads=2 --miner.etherbase=0xF3C152F925729bF10Ce2cFEA5d63268729d04a93 --http --http.addr '0.0.0.0' --allow-insecure-unlock --syncmode full --ipcpath geth-node1.ipc ```


Node2:
```geth --datadir node2 --port 30310 --bootnodes enode://<enode> --networkid 141319 --unlock  0x0CEc2ee4c45294475cF462B0461AA8251A680Df8 --password node2/password.txt  --mine --miner.threads=1 --miner.etherbase=0x0CEc2ee4c45294475cF462B0461AA8251A680Df8    --http --http.port 8550 --authrpc.port 8551 --http.addr '0.0.0.0' --allow-insecure-unlock --syncmode full --ipcpath geth-node2.ipc```

Non Miner Nodes:
Node2:
```geth --datadir node2 --port 30310 --bootnodes enode://<enode> --networkid 141319 --unlock  0x0CEc2ee4c45294475cF462B0461AA8251A680Df8 --password node2/password.txt --http --http.port 8550 --authrpc.port 8551 --http.addr '0.0.0.0' --allow-insecure-unlock --syncmode full --ipcpath geth-node2.ipc```

---
Initial Balances:
| Address                                   | Balance   |
| ----------------------------------------- | --------- |
| E94B2fc61C602cfd5F25ae2bcD1205e1136982cF | 900,000,000 |
|0CEc2ee4c45294475cF462B0461AA8251A680Df8 | 800,000,000 |

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



You can also check the balance of the current account with `eth.getBalance(eth.accounts[0])`.

---

## Send Transaction

To send a transaction to each node, use the following commands:

- Node1: `0xF3C152F925729bF10Ce2cFEA5d63268729d04a93`
- Node2: `0x0CEc2ee4c45294475cF462B0461AA8251A680Df8`
Send transaction:
To Node1 :

```eth.sendTransaction({from: eth.accounts[0], to: '0xF3C152F925729bF10Ce2cFEA5d63268729d04a93', value: 3000, gasPrice: 100 })```

To Node2 :

```eth.sendTransaction({from: eth.accounts[0], to: '0x0CEc2ee4c45294475cF462B0461AA8251A680Df8', value: 4000, gasPrice: 20 })```







##### Pending :
```txpool.status```

```txpool.content```



###### Transaction 1





```eth.getTransaction('0xd75593c6842f9bd8f5700585b92e0a5a410fcd80e2877190ce3b48067c96405e')```

```
{
  blockHash: "0x257a7ed6e4bce05b60b6e00a9fed250699f34e354d59ff447c5fcad64134302f",
  blockNumber: 18,
  chainId: "0x3931",
  from: "0xf3c152f925729bf10ce2cfea5d63268729d04a93",
  gas: 21000,
  gasPrice: 20,
  hash: "0xd75593c6842f9bd8f5700585b92e0a5a410fcd80e2877190ce3b48067c96405e",
  input: "0x",
  nonce: 0,
  r: "0xe073be995294f36dcf639edc614323b7367d1f87310519ef47c709ca54bdddf1",
  s: "0x58eb9d31a2fbed0ef25968e17ee78dd5beb001190573a7e76890db07e3ad76f",
  to: "0x0cec2ee4c45294475cf462b0461aa8251a680df8",
  transactionIndex: 0,
  type: "0x0",
  v: "0x7286",
  value: 4000
}
```





## Genesis.json
```
{
  "config": {
    "chainId": 14641,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0
  },
 "alloc": {
  "0xF3C152F925729bF10Ce2cFEA5d63268729d04a93": {
    "balance": "800000000"
  },
  "0x0CEc2ee4c45294475cF462B0461AA8251A680Df8": {
    "balance": "900000000"
  },
}
  "coinbase": "0x0000000000000000000000000000000000000000",
  "difficulty": "0x1",
  "extraData": "",
  "gasLimit": "0x2fefd8",
  "nonce": "0x0000000000000042",
  "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp": "0x00"
}


```


