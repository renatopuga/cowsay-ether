
# cowsay-ether -  Ethereum Fundamentals - hands on
FIAP - Ethereum Fundamentals




```bash
< Aula: ETHEREUM FUNDAMENTALS -
< Prof. GLAUBER DUARTE MONTEIRO >
 -----------------------------
     \   ^__^
      \  (oo)\_______
         (__)\       )\/\
            ||----w |
            ||     ||
by Renato Puga
```

## Slides

* Aula do dia 29/08/2019 - Slides no Portal do Aluno FIAP
* Aula do dia 03/09/2019 - Slides no Portal do Aluno FIAP
* Aula do dia 05/09/2019 - Slides no Portal do Aluno FIAP
	 

##  Importante

* Nunca, você me ouviu, nunca execute o comando `geth` sem a opção  `--dev` (a mainnet vem com tudo).


## Apps & Deps

```bash
# install cowsay e fortune
sudo apt install cowsay fortune

# install tree
sudo apt install tree

# install htop
sudo apt install htop
```

## install go

```bash
# voltar para home e app
cd
cd app

# download do go bin (linux)
# download do go bin (Mac) https://dl.google.com/go/go1.12.9.darwin-amd64.tar.gz
wget https://dl.google.com/go/go1.12.7.linux-amd64.tar.gz

# decompactar com tar
tar -zxvf go1.12.7.linux-amd64.tar.gz

# colocando variaveis de ambiente no ~/.bashrc
vim ~/.bashrc

# adicioanr as linhas no final do arquivo
export GOROOT=/home/ethereum-fiap/app/go
export GOPATH=$HOME/projects
export PATH=$PATH:$GOPATH/bin:$GOROOT/bin

# rodar o source para ativar as variáveis no path
source ~/.bashrc
```

## install geth

```bash
# voltar para o home e acessar o dir app
cd 
cd app

# download do geth
wget -c https://github.com/ethereum/go-ethereum/archive/v1.9.2.tar.gz

# decompactar com tar
tar -zxvf v1.9.2.tar.gz

# instalar go
cd go-ethereum-1.9.2
make all

# colocando variaveis de ambiente no ~/.bashrc
vim ~/.bashrc

# adicioanr as linhas no final do arquivo
export PATH=$PATH:/home/ethereum-fiap/app/go-ethereum-1.9.2/build/bin

# rodar o source para ativar as variáveis no path
source ~/.bashrc

# testar o geth
geth --dev

# para fechar aperte Ctrl + C
```

## Variáveis de Ambiente

```bash
export GOROOT=/home/ethereum-fiap/app/go
export GOPATH=$HOME/projects
export PATH=$PATH:$GOPATH/bin:$GOROOT/bin:/home/ethereum-fiap/app/go-ethereum-master/build/bin
```

## Run geth

```bash
# criar o diretorio
cd
mkdir ethereum-dev

# rodar geth agora com diretorio
geth --dev --datadir ~/ethereum-dev

# em outro aba do terminal execute:
cd 
tree ethereum-dev
.
├── geth
│   ├── chaindata
│   │   ├── 000002.ldb
│   │   ├── 000003.log
│   │   ├── ancient
│   │   │   ├── bodies.0000.cdat
│   │   │   ├── bodies.cidx
│   │   │   ├── diffs.0000.rdat
│   │   │   ├── diffs.ridx
│   │   │   ├── FLOCK
│   │   │   ├── hashes.0000.rdat
│   │   │   ├── hashes.ridx
│   │   │   ├── headers.0000.cdat
│   │   │   ├── headers.cidx
│   │   │   ├── receipts.0000.cdat
│   │   │   └── receipts.cidx
│   │   ├── CURRENT
│   │   ├── CURRENT.bak
│   │   ├── LOCK
│   │   ├── LOG
│   │   └── MANIFEST-000004
│   ├── LOCK
│   ├── nodekey
│   ├── nodes
│   │   ├── 000002.ldb
│   │   ├── 000003.log
│   │   ├── CURRENT
│   │   ├── CURRENT.bak
│   │   ├── LOCK
│   │   ├── LOG
│   │   └── MANIFEST-000004
│   └── transactions.rlp
├── geth.ipc
└── keystore
    └── UTC--2019-08-29T22-45-41.335123850Z--d35e2981d39ee92fa87488ae7cb642ddc706b65f

5 directories, 30 files

# Se a geth.ipc aparecer é por esta rodando.
```
	
## geth - JavaScript Console

```bash
# em uma nova aba
cd
cd ethereum-dev
geth attach ~/ethereum-dev/geth.ipc

Welcome to the Geth JavaScript console!

instance: Geth/v1.9.3-unstable/linux-amd64/go1.12.7
coinbase: 0xd35e2981d39ee92fa87488ae7cb642ddc706b65f
at block: 0 (Wed, 31 Dec 1969 21:00:00 -03)
 datadir: /home/ethereum-fiap/ethereum-dev
 modules: admin:1.0 clique:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 shh:1.0 txpool:1.0 web3:1.0

# digite web3 e aparece um monte de função: web3 é um grande JSON
> web3
{
  admin: {
    datadir: "/home/ethereum-fiap/ethereum-dev",
    nodeInfo: {
      enode: "enode://b2b3771eb248d1936d8d2b55315ed2d60cbbb9690d030cbdddbb1a46ce8ef27fb93504c22e6e8f973ddfe8672a7b69688f2277838bb76c36964b0ca0748195ce@127.0.0.1:36787?discport=0",
      enr: "enr:-JC4QLN8LHX-VkKQu5ZWGnmUUA5C999h7zzMYzQ7zz3d48aRSo0w8772ae1vz5fh5EJALVUnd2zNwzrZuS9nR9FESgcDg2V0aMfGhIdSRnaAgmlkgnY0gmlwhH8AAAGJc2VjcDI1NmsxoQKys3ceskjRk22NK1UxXtLWDLu5aQ0DDL3duxpGzo7yf4N0Y3CCj7M",
      id: "3821abddd31f092d5d01865ffa4018b4a56431209785a0a0ddfa31ab376a7bbe",
      ip: "127.0.0.1",
      listenAddr: "[::]:36787",
      name: "Geth/v1.9.3-unstable/linux-amd64/go1.12.7",
      ports: {
        discovery: 0,
        listener: 36787
      },
      protocols: {
        eth: {...},
        shh: {...}
      }
    },
....

# rodar funcoes especificas do ethereum
> web3.eth
{
  accounts: ["0xd35e2981d39ee92fa87488ae7cb642ddc706b65f"],
  blockNumber: 0,
  coinbase: "0xd35e2981d39ee92fa87488ae7cb642ddc706b65f",
  compile: {
    lll: function(),
    serpent: function(),
    solidity: function()
  },
  defaultAccount: undefined,
  defaultBlock: "latest",
  gasPrice: 1,
  hashrate: 0,
  mining: true,
  pendingTransactions: [],
  protocolVersion: "0x3f",
  syncing: false,
  call: function(),
  chainId: function(),
  contract: function(abi),
  estimateGas: function(),
  filter: function(options, callback, filterCreationErrorCallback),
...

# funcoes bem java
> console
{
  assert: function assert(),
  debug: function debug(),
  dir: function dir(),
  error: function github.com/ethereum/go-ethereum/console.(*Console).consoleOutput-fm(),
  info: function info(),
  log: function github.com/ethereum/go-ethereum/console.(*Console).consoleOutput-fm(),
  time: function time(),
  timeEnd: function timeEnd(),
  trace: function trace(),
  warn: function warn()
}
> console.log
function github.com/ethereum/go-ethereum/console.(*Console).consoleOutput-fm()

# parametros na funcao console.log
# undefined = todas execucao sem resultado é isso (coisas de Java)
> console.log(eth.accounts)
0xd35e2981d39ee92fa87488ae7cb642ddc706b65f
undefined

# variavel do tipo array
> eth.accounts
["0xd35e2981d39ee92fa87488ae7cb642ddc706b65f"]

# criando uma chave privada
> personal.newAccount('123')
"0x20d30daabbd46caa89a7115882acb65c50b4e879"

# em uma outra aba...
# apos a cricao da conta, observe o diretorio ~/ethereum-dev
cd 
cat ethereum-dev/keystore/UTC--2019-08-29T22-45-41.335123850Z--d35e2981d39ee92fa87488ae7cb642ddc706b65f

{"address":"d35e2981d39ee92fa87488ae7cb642ddc706b65f","crypto":{"cipher":"aes-128-ctr","ciphertext":"ba121626cf512ead9b672567d7ad19b5dbc5ed968eca27741ea732367cff6c6f","cipherparams":{"iv":"e03ac4a2d4e07336794d0d5c0096a212"},"kdf":"scrypt","kdfparams":{"dklen":32,"n":262144,"p":1,"r":8,"salt":"2f1af76186da1ca17b40f61e13cb89fec9e8cc292e0ae304c489e75e23423bf1"},"mac":"8a0d909683eec92f3b2ae616da2b94b41a6f343a6fb11824762a0c40b830c11d"},"id":"2cdb5492-164c-4a86-8954-bd4b8afcb202","version":3}

# Abra o Navegador e cole o resultado do cat e cole no site abaixo 
# https://jsonformatter.org/
{
  "address": "d35e2981d39ee92fa87488ae7cb642ddc706b65f",
  "crypto": {
    "cipher": "aes-128-ctr",
    "ciphertext": "ba121626cf512ead9b672567d7ad19b5dbc5ed968eca27741ea732367cff6c6f",
    "cipherparams": {
      "iv": "e03ac4a2d4e07336794d0d5c0096a212"
    },
    "kdf": "scrypt",
    "kdfparams": {
      "dklen": 32,
      "n": 262144,
      "p": 1,
      "r": 8,
      "salt": "2f1af76186da1ca17b40f61e13cb89fec9e8cc292e0ae304c489e75e23423bf1"
    },
    "mac": "8a0d909683eec92f3b2ae616da2b94b41a6f343a6fb11824762a0c40b830c11d"
  },
  "id": "2cdb5492-164c-4a86-8954-bd4b8afcb202",
  "version": 3
}

# checando o saldo
> eth.getBalance('0x20d30daabbd46caa89a7115882acb65c50b4e879')
0

# pegando salado da conta 0
> eth.getBalance(eth.accounts[0])
1.15792089237316195423570985008687907853269984665640564039457584007913129639927e+77

# chegando o resutado da funcao console.log 
> console.log(eth.sendTransaction)
function () {
        var payload = method.toPayload(Array.prototype.slice.call(arguments));
        if (payload.callback) {
            return method.requestManager.sendAsync(payload, function (err, result) {
                payload.callback(err, method.formatOutput(result));
            });
        }
        return method.formatOutput(method.requestManager.send(payload));
    }
undefined
...

# mandando 1 ether de uma conta para outra... sera ether?
> eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[1], value:1})
"0xc79ee3be0583b34e03a606158526ff25d087e1782b21bda690c3c1c0a2668677"

# verificando a transacao
	> eth.getTransaction('0xc79ee3be0583b34e03a606158526ff25d087e1782b21bda690c3c1c0a2668677')	
{
  blockHash: "0xd944caec92399c0a9b2072e90324742a4df98270f8551b5a98662eeab7e51260",
  blockNumber: 1,
  from: "0xd35e2981d39ee92fa87488ae7cb642ddc706b65f",
  gas: 21000,
  gasPrice: 1,
  hash: "0xc79ee3be0583b34e03a606158526ff25d087e1782b21bda690c3c1c0a2668677",
  input: "0x",
  nonce: 0,
  r: "0x5e51a02ec88dd7595c7723d7175b79f69ac3de94e963dfe474b92ffebddb2faf",
  s: "0x37f6bd5115134c633a54bafa66ff4d2a8830e07dd8149ddaa97f84b0657071f5",
  to: "0x20d30daabbd46caa89a7115882acb65c50b4e879",
  transactionIndex: 0,
  v: "0xa95",
  value: 1
}

# convert para valor em Wei
> web3.fromWei(eth.getBalance(eth.accounts[1]).toString(),'ether')
"0.000000000000000001"

# enviando valor correto na transacao
> eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[1], value:web3.toWei(1)})
"0xb54b42c9dab29c4ce006be7bbdc852b7eff51907d7bb2a54ba43c197ddee2e34"

# agora nao precisa usar o toString 
> web3.fromWei(eth.getBalance(eth.accounts[1]),'ether')
1.000000000000000001

# mandando 10 Wei
> eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[1], value:web3.toWei(10)})
"0xf4af7d4262ce03e318afb5d29fe7a8d14faaca999dd5582384479af90fd6e0ea"
> web3.fromWei(eth.getBalance(eth.accounts[1]),'ether')
11.000000000000000001

# mandando 100 Wei
> eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[1], value:web3.toWei(100)})
"0x1d6625eca9b00416337bc932b71a11aecadfd31ebcc278f4779ddb512d63fb52"
> web3.fromWei(eth.getBalance(eth.accounts[1]),'ether')
111.000000000000000001

# devolvendo ether para a conta... espera, erro?
> eth.sendTransaction({from:eth.accounts[1],to:eth.accounts[0], value:web3.toWei(100)})
Error: authentication needed: password or unlock
    at web3.js:3143:20
    at web3.js:6347:15
    at web3.js:5081:36
    at <anonymous>:1:1
```

```bash
#< O Goiaba, usa o Lock Account! >
# -------------------------------
#        \   ^__^
#         \  (oo)\_______
#            (__)\       )\/\
#                ||----w |
#                ||     ||
# ALERT! por seguranca o personal.unlockAccount nao fica no history do terminal
```


```bash
> personal.unlockAccount(eth.accounts[1],'123')
> eth.sendTransaction({from:eth.accounts[1],to:eth.accounts[0], value:web3.toWei(100)})
"0x5dc3e9a6b4a8cb2cf905d57ffff11cfb0d9943a6a334040a65eaf7933eea0b87"

# consultando o saldo
> web3.fromWei(eth.getBalance(eth.accounts[1]),'ether')
10.999999999999979001

# verficando o gasto de gas 
> eth.getTransaction('0x5dc3e9a6b4a8cb2cf905d57ffff11cfb0d9943a6a334040a65eaf7933eea0b87')
{
  blockHash: "0xeba549335a9da1bf52d20c4e5c4b0ad01c7655d5e0f78a51e3331b9be5b9a8c4",
  blockNumber: 5,
  from: "0x20d30daabbd46caa89a7115882acb65c50b4e879",
  gas: 21000,
  gasPrice: 1,
  hash: "0x5dc3e9a6b4a8cb2cf905d57ffff11cfb0d9943a6a334040a65eaf7933eea0b87",
  input: "0x",
  nonce: 0,
  r: "0x5292a43899bf1aadf3350a534b7213a22ea54c2b77c8de3725f7b17f79adb9e0",
  s: "0x71d165a06217c89fbbffa99ead5760997f348fb6f9205a586766c067bc765512",
  to: "0xd35e2981d39ee92fa87488ae7cb642ddc706b65f",
  transactionIndex: 0,
  v: "0xa96",
  value: 100000000000000000000
}

# bloco crescendo... bora olhar o bloco de numero 3?
> eth.getBlock(3)
{
  difficulty: 2,
  extraData: "0xd883010903846765746888676f312e31322e37856c696e757800000000000000d6102154a701ab521b3cc7e3e19b006972b71f6be6d228bcb504ec6a82816dbe1d17d8ce8fae2592e7efe3b5316a2d54662889d6b2020c4c3cdf9ca6f5f6f88c01",
  gasLimit: 6301605,
  gasUsed: 21000,
  hash: "0x37fa64f33deec453904d4a7aeb541d1a86d42414922fe0934fc02a65f0cd7a16",
  logsBloom: "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  miner: "0x0000000000000000000000000000000000000000",
  mixHash: "0x0000000000000000000000000000000000000000000000000000000000000000",
  nonce: "0x0000000000000000",
  number: 3,
  parentHash: "0x3716f65e1a5f846d3fec68a8df99b028a9115b325590e33804639dea9346b718",
  receiptsRoot: "0x056b23fbba480696b65fe5a59b8f2148a1299103c4f57df839233af2cf4ca2d2",
  sha3Uncles: "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  size: 716,
  stateRoot: "0x6d5997f53eab7a2bf04f80cffbcb163de7322163c242c6d1a5d7f28b05d3983a",
  timestamp: 1567127628,
  totalDifficulty: 7,
  transactions: ["0xf4af7d4262ce03e318afb5d29fe7a8d14faaca999dd5582384479af90fd6e0ea"],
  transactionsRoot: "0x01f58c391db63a205de0cf64da3d156cd59b805a7f6048122bd2ee991a61f033",
  uncles: []
}

```

## Docs & Tips 

* Documents Web3.js
	* [https://web3js.readthedocs.io/en/v1.2.1/](https://web3js.readthedocs.io/en/v1.2.1/)
* Convert ethereum balance getting in biginteger to ether
	* [https://ethereum.stackexchange.com/questions/32208/convert-ethereum-balance-getting-in-biginteger-to-ether](https://ethereum.stackexchange.com/questions/32208/convert-ethereum-balance-getting-in-biginteger-to-ether)
* unlockAccount
	*  [https://web3js.readthedocs.io/en/v1.2.1/web3-eth-personal.html#unlockaccount](https://web3js.readthedocs.io/en/v1.2.1/web3-eth-personal.html#unlockaccount)
* Etherscan - Maior visualizador de transações de Ether de todos os tempos
	*  [https://etherscan.io/](https://etherscan.io/)
		

## Continuação.... Dia 03

Carregar a VM e abrir duas abas no terminal:

* Terminal: aba 1

```bash
 geth --dev --datadir ~/ethereum-dev/ 
```

* Terminal: aba 2

```bash
geth  attach ~/ethereum-dev/geth.ipc 
Welcome to the Geth JavaScript console!

instance: Geth/v1.9.3-unstable/linux-amd64/go1.12.7
coinbase: 0xd35e2981d39ee92fa87488ae7cb642ddc706b65f
at block: 0 (Wed, 31 Dec 1969 21:00:00 -03)
 datadir: /home/ethereum-fiap/ethereum-dev
 modules: admin:1.0 clique:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 shh:1.0 txpool:1.0 web3:1.0

```

## Geth  - Funções

```java
>function checkAllBalances(){
	var totalBal=0;
	for (var acctNum in eth.accounts) {
		var acct = eth.accounts[acctNum];
		var acctBal = web3.fromWei(eth.getBalance(acct).toString(),"ether");
		totalBal += parseFloat(acctBal);
		console.log("eth.accounts["+ acctNum +"]:\t" + acct + "\tbalance:" + acctBal + "ether");
	}
	console.log("Total balance: " + totalBal + "ether");
	};

undefined
> checkAllBalances()
eth.accounts[0]:	0xd35e2981d39ee92fa87488ae7cb642ddc706b65f	balance:115792089237316195423570985008687907853269984665640564039457.584007913129639927ether
eth.accounts[1]:	0x20d30daabbd46caa89a7115882acb65c50b4e879	balance:0ether
Total balance: 1.157920892373162e+59ether
undefined	
```

Salve essa função em um arquivo chamado `saldos.js` e chame ele no terminal com a função `loadScript()`:

```bash
# passe o caminho completo até o arquivo saldos.js
> loadScript("/home/ethereum-fiap/saldos.js")
true
```

## Geth - Scripts	

Crie uma função **depositar** que receba um valor de ether e um endereço e realize a transferência para o endereço:

```bash
 _____________________________________
/ Goiabinha, libere sempre a origem:  \
| personal.unlockAccount(origem,'123') /
\-------------------------------------/
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

```bash

> function depositar (valor, origem, destino) {
eth.sendTransaction({from:origem,to:destino, value:web3.toWei(valor)});
console.log(web3.fromWei(eth.getBalance(destino).toString(),"ether"));
};	

> depositar(1,eth.accounts[0], eth.accounts[1])
6
undefined
> depositar(1,eth.accounts[0], eth.accounts[1])
8
undefined
> depositar(1,eth.accounts[0], eth.accounts[1])
9
undefined
> depositar(1,eth.accounts[1], eth.accounts[0])

```

## Fechar os geth tudo

Agora vamos excecutar o comando `geth` com a opção `--testenet`. 
Aqui vamos ter o mais próximo do real de mantagem de blocos.

```bash
# voltando para o home
cd 

# rodando o geth com a opcao --testnet
geth --testnet

WARN [09-03|20:55:27.746] Sanitizing cache to Go's GC limits       provided=1024 updated=1000
INFO [09-03|20:55:27.747] Maximum peer count                       ETH=50 LES=0 total=50
INFO [09-03|20:55:27.748] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
INFO [09-03|20:55:27.749] Starting peer-to-peer node               instance=Geth/v1.9.3-unstable/linux-amd64/go1.12.7
INFO [09-03|20:55:27.751] Allocated trie memory caches             clean=250.00MiB dirty=250.00MiB
INFO [09-03|20:55:27.751] Allocated cache and file handles         database=/home/ethereum-fiap/.ethereum/testnet/geth/chaindata cache=500.00MiB handles=524288
INFO [09-03|20:55:27.822] Opened ancient database                  database=/home/ethereum-fiap/.ethereum/testnet/geth/chaindata/ancient
INFO [09-03|20:55:27.827] Persisted trie from memory database      nodes=355 size=50.67KiB time=616.761µs gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [09-03|20:55:27.830] Initialised chain configuration          config="{ChainID: 3 Homestead: 0 DAO: <nil> DAOSupport: true EIP150: 0 EIP155: 10 EIP158: 10 Byzantium: 1700000 Constantinople: 4230000 Petersburg: 4939394 Istanbul: <nil> Engine: ethash}"
INFO [09-03|20:55:27.830] Disk storage enabled for ethash caches   dir=/home/ethereum-fiap/.ethereum/testnet/geth/ethash count=3
INFO [09-03|20:55:27.830] Disk storage enabled for ethash DAGs     dir=/home/ethereum-fiap/.ethash count=2
INFO [09-03|20:55:27.830] Initialising Ethereum protocol           versions=[63] network=3 dbversion=7
INFO [09-03|20:55:27.882] Loaded most recent local header          number=0 hash=419410…ca4a2d td=1048576 age=50y4mo3w
INFO [09-03|20:55:27.884] Loaded most recent local full block      number=0 hash=419410…ca4a2d td=1048576 age=50y4mo3w
INFO [09-03|20:55:27.884] Loaded most recent local fast block      number=0 hash=419410…ca4a2d td=1048576 age=50y4mo3w
INFO [09-03|20:55:27.884] Loaded local transaction journal         transactions=0 dropped=0
INFO [09-03|20:55:27.890] Regenerated local transaction journal    transactions=0 accounts=0
INFO [09-03|20:55:27.899] Allocated fast sync bloom                size=500.00MiB
INFO [09-03|20:55:27.903] Initialized fast sync bloom              items=355 errorrate=0.000 elapsed=2.026ms
INFO [09-03|20:55:27.933] New local node record                    seq=15 id=606ed001a2ff01f1 ip=127.0.0.1 udp=30303 tcp=30303
INFO [09-03|20:55:27.934] IPC endpoint opened                      url=/home/ethereum-fiap/.ethereum/testnet/geth.ipc
INFO [09-03|20:55:27.940] Started P2P networking                   self=enode://b7cd8b1529aabfbd6e48df969174839e50b0f22c7dcbb8469e7f0d758f1154d0930bb9f7c7f0010f0f9a1d5c76eeb2ce30f7eeba037eaa5eb0286c8307c7d8b1@127.0.0.1:30303
...
```

```bash
 ______________________________
< Para fechar o processo acima >
< digite Ctrl + C >
 -------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

### Os principais problemas quando nos aproximamos da Mainnet:

* Tamanho (problemas no disco)
*  Banda de Rede


## Geth - Ropsten

Abra um novo terminal e reinicie o geth. Aqui ele começa a ir atrás de nós P2P e conectar-se a rede pela porta UDP 30303. Se essa porta não estiver livre, não consegue se conectar em nenhum peer da rede.

Mas da para sair por outro porta? Sim, você precisa mudar a porta!

```bash
geth --testnet --syncmode "light"

INFO [09-03|21:00:15.189] Dropping default light client cache      provided=1024 updated=128
INFO [09-03|21:00:15.190] Maximum peer count                       ETH=0 LES=100 total=50
INFO [09-03|21:00:15.190] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
INFO [09-03|21:00:15.191] Starting peer-to-peer node               instance=Geth/v1.9.3-unstable/linux-amd64/go1.12.7
INFO [09-03|21:00:15.191] Allocated cache and file handles         database=/home/ethereum-fiap/.ethereum/testnet/geth/lightchaindata cache=64.00MiB handles=524288
INFO [09-03|21:00:15.239] Writing custom genesis block 
INFO [09-03|21:00:15.246] Persisted trie from memory database      nodes=355 size=50.67KiB time=1.1499ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [09-03|21:00:15.247] Initialised chain configuration          config="{ChainID: 3 Homestead: 0 DAO: <nil> DAOSupport: true EIP150: 0 EIP155: 10 EIP158: 10 Byzantium: 1700000 Constantinople: 4230000 Petersburg: 4939394 Istanbul: <nil> Engine: ethash}"
INFO [09-03|21:00:15.247] Disk storage enabled for ethash caches   dir=/home/ethereum-fiap/.ethereum/testnet/geth/ethash count=3
INFO [09-03|21:00:15.247] Disk storage enabled for ethash DAGs     dir=/home/ethereum-fiap/.ethash count=2
INFO [09-03|21:00:15.270] Added trusted checkpoint                 block=6160383 hash=7d6db6…d0b07d
INFO [09-03|21:00:15.270] Loaded most recent local header          number=0 hash=419410…ca4a2d td=1048576 age=50y4mo3w
INFO [09-03|21:00:15.270] Configured checkpoint registrar          address=0xEF79475013f154E6A65b54cB2742867791bf0B84 signers=5 threshold=2
INFO [09-03|21:00:15.293] UDP listener up                          net=enode://b7cd8b1529aabfbd6e48df969174839e50b0f22c7dcbb8469e7f0d758f1154d0930bb9f7c7f0010f0f9a1d5c76eeb2ce30f7eeba037eaa5eb0286c8307c7d8b1@[::]:30303
WARN [09-03|21:00:15.299] Light client mode is an experimental feature 
INFO [09-03|21:00:15.301] IPC endpoint opened                      url=/home/ethereum-fiap/.ethereum/testnet/geth.ipc
INFO [09-03|21:00:15.302] New local node record                    seq=19 id=606ed001a2ff01f1 ip=127.0.0.1 udp=30303 tcp=30303
INFO [09-03|21:00:15.302] Started P2P networking                   self=enode://b7cd8b1529aabfbd6e48df969174839e50b0f22c7dcbb8469e7f0d758f1154d0930bb9f7c7f0010f0f9a1d5c76eeb2ce30f7eeba037eaa5eb0286c8307c7d8b1@127.0.0.1:30303
WARN [09-03|21:00:57.784] Verified advertised checkpoint           peer=a051b87c7195c2c1c263e975ac861f98f9633dc1de2c310d5ff9f2e909c72b14 signers=2
INFO [09-03|21:00:57.784] Added trusted checkpoint                 block=6160383 hash=7d6db6…d0b07d
INFO [09-03|21:00:58.030] Updated latest header based on CHT       number=6160383 hash=7d6db6…d0b07d age=3w3d22h
INFO [09-03|21:00:58.030] Block synchronisation started 
INFO [09-03|21:01:07.413] Imported new block headers               count=192 elapsed=3.089s number=6160575 hash=c8eb64…053aa9 age=3w3d21h
INFO [09-03|21:01:08.706] Generating ethash verification cache     epoch=206 percentage=80 elapsed=3.058s
INFO [09-03|21:01:09.446] Imported new block headers               count=192 elapsed=2.029s number=6160767 hash=9285bf…c7a920 age=3w3d21h
INFO [09-03|21:01:09.690] Generated ethash verification cache      epoch=206 elapsed=4.042s
INFO [09-03|21:01:14.246] Imported new block headers               count=960 elapsed=4.788s number=6161727 hash=4a97c3…5d6122 age=3w3d17h
INFO [09-03|21:01:16.331] Imported new block headers               count=576 elapsed=2.076s number=6162303 hash=6aa000…735cca age=3w3d15h
INFO [09-03|21:01:25.213] Imported new block headers               count=2048 elapsed=8.870s number=6164351 hash=b24de2…f8643e age=3w3d7h
INFO [09-03|21:01:29.506] Imported new block headers               count=832  elapsed=4.270s number=6165183 hash=383545…7cff11 age=3w3d4h
INFO [09-03|21:01:35.141] Imported new block headers               count=1344 elapsed=5.585s number=6166527 hash=03fcb4…a8cd0c age=3w2d23h
INFO [09-03|21:01:43.418] Imported new block headers               count=2048 elapsed=8.259s number=6168575 hash=a9a057…00a50e age=3w2d16h

# em outra aba execute
# voltar para home
cd

# rodandno geth agora com testenet
geth attach ~/.ethereum/testnet/geth.ipc 

> admin.peers
[{
    caps: ["eth/63", "les/2", "les/3"],
    enode: "enode://053d2f57829e5785d10697fa6c5333e4d98cc564dbadd87805fd4fedeb09cbcb642306e3a73bd4191b27f821fb442fcf964317d6a520b29651e7dd09d1beb0ec@79.98.29.154:30303",
    id: "a051b87c7195c2c1c263e975ac861f98f9633dc1de2c310d5ff9f2e909c72b14",
    name: "Geth/v1.9.3-stable-cfbb969d/linux-amd64/go1.11.5",
    network: {
      inbound: false,
      localAddress: "10.0.2.15:33292",
      remoteAddress: "79.98.29.154:30303",
      static: true,
      trusted: false
    },
    protocols: {
      les: {
        difficulty: 22666369940700870,
        head: "19e1af0fe7abb57eb2fefbe9466263014dc7b1b3b719c31b835f1747458e7ccb",
        version: 3
      }
    }
}]
```

```bash
 ___________________________
< Estamos mesmo na Testnet? >
 ---------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

Podemos verificar qual a altura do bloco com `eth.blockNumber`:

```bash
> eth.blockNumber
6322813

# verificando contas existentes
> eth.accounts
[]

# criando uma conta nova na testnet
>personal.newAccount('123')
"0xb5ab638c6ffe0ebdd3edaea35724501d0764b776"

# depois de enviar no MetaMask teste:
> web3.fromWei(eth.getBalance(eth.accounts[0]))
1
```

## Geth - Gerenciamento de Contas

Vá até o MetaMask e copie a chave privada (PERIGO... PERIGO... PERIGO).

```bash
# copiar a chave privada no MetaMask e copiar a chave privada e salvar no arquivo metamask.key
geth account import --datadir ~/.ethereum/testnet metamask.key
INFO [09-03|21:41:49.560] Maximum peer count                       ETH=50 LES=0 total=50
INFO [09-03|21:41:49.560] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
Your new account is locked with a password. Please give a password. Do not forget this password.
Password: 
Repeat password: 
Address: {cd1f55318de39bd2e8d32a7a949ca4bb7c865c88}

# listando as contas
geth account list
INFO [09-03|21:47:31.297] Maximum peer count                       ETH=50 LES=0 total=50
INFO [09-03|21:47:31.297] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"

# listando as contas agora no datadir do testenet
geth account list --datadir ~/.ethereum/testnet
ethereum-fiap@ethereum-fiap:~$ geth account list --datadir ~/.ethereum/testnet
INFO [09-03|21:47:43.095] Maximum peer count                       ETH=50 LES=0 total=50
INFO [09-03|21:47:43.095] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
Account #0: {b5ab638c6ffe0ebdd3edaea35724501d0764b776} keystore:///home/ethereum-fiap/.ethereum/testnet/keystore/UTC--2019-09-04T00-18-49.337283662Z--b5ab638c6ffe0ebdd3edaea35724501d0764b776
Account #1: {cd1f55318de39bd2e8d32a7a949ca4bb7c865c88} keystore:///home/ethereum-fiap/.ethereum/testnet/keystore/UTC--2019-09-04T00-41-52.425232849Z--cd1f55318de39bd2e8d32a7a949ca4bb7c865c88
```

```bash
 _____________________________________
/ Agora, vc que é bem Goiaba, apaga o \
\ metamask.key!                       /
 -------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

## Geth - Rede de Teste Prática
Enviar um ether para o colequinha.

*  Terminal Aba 1:

```bash
 geth --testnet --syncmode "light"
```
* Terminal Aba 2:

```bash
# geth neles
geth attach ~/.ethereum/testnet/geth.ipc 

# carregando a funcao depositar (poderia ter salvo no arquivo)
> function depositar (valor, origem, destino) {
eth.sendTransaction({from:origem,to:destino, value:web3.toWei(valor)});
console.log(web3.fromWei(eth.getBalance(destino).toString(),"ether"));
};	

# unlock a continha
> personal.unlockAccount("0xCd1f55318De39Bd2e8D32A7A949CA4Bb7c865c88",'123')
true

# depositar origem -> destino (retona o valor da destino)
> depositar(0.032,"0xCd1f55318De39Bd2e8D32A7A949CA4Bb7c865c88","91296e454eaa17258b5f13ceb3ba7c863670f325")
2.99958
undefined
```

```bash
/ No Gas no Gain! Se tiver 1 ether não \
\ vai conseguir enviar maluco!         /
 --------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

## Geth - Rede Teste 2
Faça a transação  alterando o gas e gasPrice.


### Mudando o valor de gas na função depo_gas_change()

```bash
function depo_gas_change (valor, origem, destino, gas) {
eth.sendTransaction({from:origem,to:destino, value:web3.toWei(valor), gas:gas});
console.log(web3.fromWei(eth.getBalance(destino).toString(),"ether"));
};

# unlock a continha
> personal.unlockAccount(eth.accounts[1],'123')
true

# depositar origem -> destino (retona o valor da destino)
> depo_gas_change(0.032,eth.accounts[1],eth.accounts[0],18000)
Error: intrinsic gas too low
    at web3.js:3143:20
    at web3.js:6347:15
    at web3.js:5081:36
    at depo_gas_change (<anonymous>:2:1)
    at <anonymous>:1:1

> depo_gas_change(0.032,eth.accounts[1],eth.accounts[0],21000)
1.032

```

### Mudando o valor de gas na função depo_gasPrice_change()

```bash
function depo_gasPrice_change (valor, origem, destino, gasprice) {
eth.sendTransaction({from:origem,to:destino, value:web3.toWei(valor), gasPrice:web3.toWei(gasprice, "gwei")});
console.log(web3.fromWei(eth.getBalance(destino).toString(),"ether"));
};

# unlock a continha
> personal.unlockAccount(eth.accounts[1],'123')
true

# depositar origem -> destino (retona o valor da destino)
> depo_gasPrice_change(0.032,eth.accounts[1],eth.accounts[0],0.0005)
1.064
```
### Mudando o valor de Gas na função depo_gasPrice_nonce_change()

```bash
function depo_gasPrice_nonce_change (valor, origem, destino, gasprice, nonce) {
eth.sendTransaction({from:origem,to:destino, value:web3.toWei(valor), gasPrice:web3.toWei(gasprice, "gwei"), nonce:nonce});
console.log(web3.fromWei(eth.getBalance(destino).toString(),"ether"));
};

# unlock a continha
> personal.unlockAccount(eth.accounts[1],'123')
true

# descobrir o nonce 
> eth.getTransactionCount(eth.accounts[1])
28

# depositar origem -> destino (retona o valor da destino)
> depo_gasPrice_nonce_change(0.032,eth.accounts[1],eth.accounts[0],0.0005,29)
1.064
```

```bash
 _________
< Buguei! >
 ---------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```
## Geth - RPC

Nesse modo a gente não se preocupa com o modo https (menos seguro), mas para acessar esses nodes nós precisamos pelo menos do domain e o rpc no bash não carrega por padrão as bibliotecas, por isso declaramos elas por `rpcapi` .

```bash
 _____________________________________________
< Feche todos os consoles aberto, se existir! >
 --------------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

```bash
cd 
geth --testnet --syncmode "light" --rpc --rpccorsdomain '*' --rpcapi web3,eth,personal,admin,net,db

INFO [09-05|19:38:32.426] Dropping default light client cache      provided=1024 updated=128
INFO [09-05|19:38:32.428] Maximum peer count                       ETH=0 LES=100 total=50
INFO [09-05|19:38:32.428] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
INFO [09-05|19:38:32.494] Starting peer-to-peer node               instance=Geth/v1.9.3-unstable/linux-amd64/go1.12.7
INFO [09-05|19:38:32.496] Allocated cache and file handles         database=/home/ethereum-fiap/.ethereum/testnet/geth/lightchaindata cache=64.00MiB handles=524288
INFO [09-05|19:38:32.701] Persisted trie from memory database      nodes=355 size=50.67KiB time=510.592µs gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [09-05|19:38:32.701] Initialised chain configuration          config="{ChainID: 3 Homestead: 0 DAO: <nil> DAOSupport: true EIP150: 0 EIP155: 10 EIP158: 10 Byzantium: 1700000 Constantinople: 4230000 Petersburg: 4939394 Istanbul: <nil> Engine: ethash}"
INFO [09-05|19:38:32.702] Disk storage enabled for ethash caches   dir=/home/ethereum-fiap/.ethereum/testnet/geth/ethash count=3
INFO [09-05|19:38:32.702] Disk storage enabled for ethash DAGs     dir=/home/ethereum-fiap/.ethash count=2
INFO [09-05|19:38:32.787] Added trusted checkpoint                 block=6160383 hash=7d6db6…d0b07d
INFO [09-05|19:38:32.787] Loaded most recent local header          number=6323250 hash=4503b9…c6c0d7 td=22669098121385181 age=1d20h41m
INFO [09-05|19:38:32.794] Configured checkpoint registrar          address=0xEF79475013f154E6A65b54cB2742867791bf0B84 signers=5 threshold=2
INFO [09-05|19:38:32.851] UDP listener up                          net=enode://b7cd8b1529aabfbd6e48df969174839e50b0f22c7dcbb8469e7f0d758f1154d0930bb9f7c7f0010f0f9a1d5c76eeb2ce30f7eeba037eaa5eb0286c8307c7d8b1@[::]:30303
WARN [09-05|19:38:32.852] Light client mode is an experimental feature 
INFO [09-05|19:38:32.857] IPC endpoint opened                      url=/home/ethereum-fiap/.ethereum/testnet/geth.ipc
INFO [09-05|19:38:32.866] HTTP endpoint opened                     url=http://127.0.0.1:8545 cors=* vhosts=localhost
INFO [09-05|19:38:32.867] New local node record                    seq=23 id=606ed001a2ff01f1 ip=127.0.0.1 udp=30303 tcp=30303
INFO [09-05|19:38:32.867] Started P2P networking                   self=enode://b7cd8b1529aabfbd6e48df969174839e50b0f22c7dcbb8469e7f0d758f1154d0930bb9f7c7f0010f0f9a1d5c76eeb2ce30f7eeba037eaa5eb0286c8307c7d8b1@127.0.0.1:30303
INFO [09-05|19:38:33.522] Block synchronisation started 

# executando geth attach
> geth attach http://localhost:8545
Welcome to the Geth JavaScript console!

instance: Geth/v1.9.3-unstable/linux-amd64/go1.12.7
at block: 6335894 (Thu, 05 Sep 2019 19:47:08 -03)
 datadir: /home/ethereum-fiap/.ethereum/testnet
 modules: admin:1.0 eth:1.0 net:1.0 personal:1.0 rpc:1.0 web3:1.0

> 

```

```bash
 ______________________________
< Quando usamos RPC precisamos >
< pensar em segurança! >
 -------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

## Geth - JSON RPC

```bash
# listando as contas
> eth.accounts
["0xb5ab638c6ffe0ebdd3edaea35724501d0764b776", "0xcd1f55318de39bd2e8d32a7a949ca4bb7c865c88"]

# colocando umas das contas no valor params:
> curl -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0","method":"eth_getBalance","params":["0xb5ab638c6ffe0ebdd3edaea35724501d0764b776", "latest"],"id":1}' http://localhost:8545
```

* Abra um novo terminal linux

``` bash
ethereum-fiap@ethereum-fiap:~$ curl -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0","method":"eth_getBalance","params":["0xb5ab638c6ffe0ebdd3edaea35724501d0764b776", "latest"],"id":1}' http://localhost:8545
{"jsonrpc":"2.0","id":1,"result":"0xec4165cd9040000"}

```

```bash
/ Abra o MetaMask e seleciona a rede     \
| Localhost 8545 e envie ethers para uma |
\ conta no geth                          /
 ----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

## Geth -  RPC + MetaMask

Veja as imagens de como acessar o MetaMask nos slides de número 26-30 da Aula 03:

* FIAP_MBA_Blockchain_Ethereum-Fundamentals_Aula-3


## Geth - Projeto 01

Abra um terminal no linux e verifique a versão do node com a opção `--version`:

```bash
# verificando o node
node --version
v8.15.1

# criando diretorio ethereum-web3 no home
cd
mkdir ethereum-web3
cd ethereum-web3
```

```bash
 _________________________________
/ Node é um tecnologia para rodar \
\ back-end                        /
 ---------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

```bash
# verificando o node
node --version
v8.15.1

# criando diretorio ethereum-web3 no home
cd
mkdir ethereum-web3
cd ethereum-web3

# iniciar o node
# tecla ENTER para todas as perguntas
npm init

This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (ethereum-web3) 
version: (1.0.0) 
description: 
entry point: (index.js) 
test command: 
git repository: 
keywords: 
author: 
license: (ISC) 
About to write to /home/ethereum-fiap/ethereum-web3/package.json:

{
  "name": "ethereum-web3",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes) 

# agora digite code no diretorio atual
code .

# agora vamos instalar o web3
npm install web3

npm install web3
npm ERR! code ENOGIT
npm ERR! Error while executing:
npm ERR! undefined ls-remote -h -t ssh://git@github.com/web3-js/WebSocket-Node.git
npm ERR! 
npm ERR! undefined
npm ERR! No git binary found in $PATH
npm ERR! 
npm ERR! Failed using git.
npm ERR! Please check if you have git installed and in your PATH.

npm ERR! A complete log of this run can be found in:
npm ERR!     /home/ethereum-fiap/.npm/_logs/2019-09-05T23_38_23_513Z-debug.log

```
```bash
 _________________________________
< Deu erro de Git! Bora instalar? >
 ---------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

```bash
# instalando o git
sudo apt install git

[sudo] password for ethereum-fiap: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  brave-keyring linux-headers-4.15.0-45 linux-headers-4.15.0-45-generic linux-image-4.15.0-45-generic linux-modules-4.15.0-45-generic
  linux-modules-extra-4.15.0-45-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk gitweb git-arch git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 87 not upgraded.
Need to get 3.932 kB of archives.
After this operation, 25,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://br.archive.ubuntu.com/ubuntu xenial/main amd64 liberror-perl all 0.17-1.2 [19,6 kB]
Get:2 http://br.archive.ubuntu.com/ubuntu xenial-updates/main amd64 git-man all 1:2.7.4-0ubuntu1.6 [736 kB]
Get:3 http://br.archive.ubuntu.com/ubuntu xenial-updates/main amd64 git amd64 1:2.7.4-0ubuntu1.6 [3.176 kB]
Fetched 3.932 kB in 0s (4.005 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 253870 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17-1.2_all.deb ...
Unpacking liberror-perl (0.17-1.2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.7.4-0ubuntu1.6_all.deb ...
Unpacking git-man (1:2.7.4-0ubuntu1.6) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.7.4-0ubuntu1.6_amd64.deb ...
Unpacking git (1:2.7.4-0ubuntu1.6) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up liberror-perl (0.17-1.2) ...
Setting up git-man (1:2.7.4-0ubuntu1.6) ...
Setting up git (1:2.7.4-0ubuntu1.6) ...

# agora com o git instalado vamos instalar o web3 com o npm
npm install web3

> sha3@1.2.3 install /home/ethereum-fiap/ethereum-web3/node_modules/sha3
> node-gyp rebuild

make: Entering directory '/home/ethereum-fiap/ethereum-web3/node_modules/sha3/build'
  CXX(target) Release/obj.target/sha3/src/addon.o
  CXX(target) Release/obj.target/sha3/src/displayIntermediateValues.o
  CXX(target) Release/obj.target/sha3/src/KeccakF-1600-reference.o
  CXX(target) Release/obj.target/sha3/src/KeccakNISTInterface.o
  CXX(target) Release/obj.target/sha3/src/KeccakSponge.o
  SOLINK_MODULE(target) Release/obj.target/sha3.node
  COPY Release/sha3.node
make: Leaving directory '/home/ethereum-fiap/ethereum-web3/node_modules/sha3/build'

> websocket@1.0.29 install /home/ethereum-fiap/ethereum-web3/node_modules/websocket
> (node-gyp rebuild 2> builderror.log) || (exit 0)

make: Entering directory '/home/ethereum-fiap/ethereum-web3/node_modules/websocket/build'
  CXX(target) Release/obj.target/bufferutil/src/bufferutil.o
  SOLINK_MODULE(target) Release/obj.target/bufferutil.node
  COPY Release/bufferutil.node
  CXX(target) Release/obj.target/validation/src/validation.o
  SOLINK_MODULE(target) Release/obj.target/validation.node
  COPY Release/validation.node
make: Leaving directory '/home/ethereum-fiap/ethereum-web3/node_modules/websocket/build'
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN ethereum-web3@1.0.0 No description
npm WARN ethereum-web3@1.0.0 No repository field.

+ web3@1.2.1
added 342 packages from 219 contributors and audited 30411 packages in 29.546s
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details

```

## Geth - balance.js

Copie o último slide da Aula 04, crie um arquivo novo no Visual Studio Code com o nome de `balance.js` e salve o código:

* code balance.js
```java
const  args  =  process.argv.slice(2)
const  Web3  =  require('web3');
const  web3  =  new  Web3(new Web3.providers.HttpProvider('http://localhost:8545'));

if(!args[0]){
console.log("Passe um endereço para consulta")
return
}
web3.eth.getBalance(args[0])
.then(balance  => {console.log(`Saldo de ${args[0]}: `  +  web3.utils.fromWei(balance))
})
.catch( err  =>  console.error(err))
```

* Agora no console do linux execute o balance.js com o comando node:


```bash
node balance.js 
/home/ethereum-fiap/ethereum-web3/balance.js:6
console.log('Passe um endereço para consulta’)
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

SyntaxError: Invalid or unexpected token
    at createScript (vm.js:80:10)
    at Object.runInThisContext (vm.js:139:10)
    at Module._compile (module.js:617:28)
    at Object.Module._extensions..js (module.js:664:10)
    at Module.load (module.js:566:32)
    at tryModuleLoad (module.js:506:12)
    at Function.Module._load (module.js:498:3)
    at Function.Module.runMain (module.js:694:10)
    at startup (bootstrap_node.js:204:16)
    at bootstrap_node.js:625:3
```

```bash
 _______________________________________
/ Pegadinha da aspa simple do Glauber!  \
\ Edita o código, salva e roda de novo. /
 ---------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```
	
```bash
# no terminal do linux no diretorio ethereum-web3 rode o script balance.js
node balance.js 

You can improve web3's peformance when running Node.js versions older than 10.5.0 by installing the (deprecated) scrypt package in your project
Passe um endereço para consulta

# rodando com um endereco valido
node balance.js 0xb5ab638c6ffe0ebdd3edaea35724501d0764b776
You can improve web3's peformance when running Node.js versions older than 10.5.0 by installing the (deprecated) scrypt package in your project
Saldo de 0xb5ab638c6ffe0ebdd3edaea35724501d0764b776: 1.0661

```

```bash
 ________________________________
/ O Visual Studio Code não salva \
\ automaticamente. Fique atento! /
 --------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```


## sendEther.js - trabalho
Objetivo desse trabalho é desenvolver um script para enviar ether para dois endereços diferentes.

Para vencer o problema de `unlockAccounts` eu tive que parar o `geth rpc web3` e o `geth attach` que estava rodando e adicionar mais uma opção `--allow-insecure-unlock`. Feito isso, podemos executar novamente o geth e testar o script sendEther.js.

* Aba 1 do terminal linux

```bash
# rodando com a opcao --allow-insecure-unlock
 geth --testnet --syncmode "light" --rpc --rpccorsdomain '*' --rpcapi web3,eth,personal,admin,net,db --allow-insecure-unlock
```

```bash
 _________________________________________
/ Sending your account password over an   \
| unsecured HTTP RPC connection is highly |
\ unsecure                                /
 -----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

* Aba 2 do terminal linux

```bash
# rodando novamente o geth attach
geth attach http://localhost:8545

Welcome to the Geth JavaScript console!

instance: Geth/v1.9.3-unstable/linux-amd64/go1.12.7
at block: 6336586 (Thu, 05 Sep 2019 22:19:23 -03)
 datadir: /home/ethereum-fiap/.ethereum/testnet
 modules: admin:1.0 eth:1.0 net:1.0 personal:1.0 rpc:1.0 web3:1.0

# unloack para o endereço
> personal.unlockAccount("0xcd1f55318de39bd2e8d32a7a949ca4bb7c865c88", "123", 600)
true

```


Com o ambiente geth rpc web3 rodando, abra um terminal no diretorio ethereum-web3, crie no Visual Studio Code um novo arquivo chamado `sendEther.js` e com o código abaixo eu espero enviar ethers para um endereço meu hardcode.

* Em uma nova aba terminal do linux

```bash
# voltando para o home
cd

# acessando o diretorio ethereum-web3
cd ethereum-web3

# executando o script sendEther.js
# valor: 0.032
# destino 1: 0xb5ab638c6ffe0ebdd3edaea35724501d0764b776
# destino 2: 0x35b4439277e3e6543e08e7f908d9087110c7921b

node sendEther.js 0.032 0xb5ab638c6ffe0ebdd3edaea35724501d0764b776 0x35b4439277e3e6543e08e7f908d9087110c7921b


You can improve web3's peformance when running Node.js versions older than 10.5.0 by installing the (deprecated) scrypt package in your project
Saldo de 0xb5ab638c6ffe0ebdd3edaea35724501d0764b776: 1.0981
Saldo de 0x35b4439277e3e6543e08e7f908d9087110c7921b: 0.032

```

```bash
 ___________________________
/ Pensa em um código porco! \
 ----------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

* code sendEther.js

```bash
const args = process.argv.slice(2)
const Web3 = require('web3');
const web3 = new Web3(new
Web3.providers.HttpProvider('http://localhost:8545'));

if(!args[0] && !args[1] && !$args[2]){   
console.log("Passe na ordem: 1 valor (ether) e 2 Endereços para receber o deposito")
return
}

// funcao para depositar
function depositar (valor, origem, destino) {
    web3.eth.sendTransaction({from:origem,to:destino, value:web3.utils.toWei(valor)})
  //     console.log(web3.utils.fromWei(web3.eth.getBalance(destino),"ether"));
}


// unlockAccount
web3.eth.personal.unlockAccount("0xCd1f55318De39Bd2e8D32A7A949CA4Bb7c865c88","123",600);

// enviar para as contas usando a funcao   
depositar(args[0],"0xCd1f55318De39Bd2e8D32A7A949CA4Bb7c865c88",args[1])
depositar(args[0],"0xCd1f55318De39Bd2e8D32A7A949CA4Bb7c865c88",args[2])

// balanco da primeira conta
web3.eth.getBalance(args[1])
.then(balance => {
console.log(`Saldo de ${args[1]}: ` + web3.utils.fromWei(balance))
})
.catch( err => console.error(err))

// balanco da segunda conta
web3.eth.getBalance(args[2])
.then(balance => {
console.log(`Saldo de ${args[2]}: ` + web3.utils.fromWei(balance))
})
.catch( err => console.error(err))
```


