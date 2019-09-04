# cowsay-ether -  Ethereum Fundamentals - hands on
FIAP - Ethereum Fundamentals

	< Aula: ETHEREUM FUNDAMENTALS -
	 Prof. GLAUBER DUARTE MONTEIRO >
	 -----------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
	by Renato Puga

## Slides

* Aula do dia 29/08/2019 - Slides no Portal do Aluno FIAP
* Aula do dia 03/09/2019 - Slides no Portal do Aluno FIAP
	 

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

# download do go
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

#< O Goiaba, usa o Lock Account! >
# -------------------------------
#        \   ^__^
#         \  (oo)\_______
#            (__)\       )\/\
#                ||----w |
#                ||     ||
# ALERT! por seguranca o personal.unlockAccount nao fica no history do terminal
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

#/ Goiabinha, libere sempre a origem:  \
#| personal.unlockAccount(origem,'123') /
#\-------------------------------------/
#        \   ^__^
#         \  (oo)\_______
#            (__)\       )\/\
#                ||----w |
#                ||     ||


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










