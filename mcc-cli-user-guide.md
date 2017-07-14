#MCC-CLI User Guide
---
#Index

* [0 MCC-CLI Overview](#0 MCC-CLI Overview)
* [1 MCC-CLI Installation](#1 MCC-CLI Installation)
* [2 MCC-CLI Syntax](#2 Command Syntax)
* [3 MCC-CLI Option Description](#3 Option Description)
	* [3.1 MCC-CLI Print Help Information](#31 MCC-CLI Print Help Information)
	* [3.2 Print MCC-CLI Version Information](#32 Print Version)
	* [3.3 Set the host name or IP address](#33 Set Host)
	* [3.4 Set the port number of Target MCC Server](#34 Set Port)
	* [3.5 Set Main Chain](#35 Set Main Chain)
* [4 MCC-CLI Supported Commands](#4 MCC Supported Commands)
	* [4.1 Get the Blockchain Height](#41 Get Block Height)
	* [4.2 Get Blockchain status](#42 Blockchain Status)
	* [4.3 Get Account Information by Password](#43 get account info)
	* [4.4 Get account information by Public Key](#44 getAccountByPublicKey)
	* [4.5 Get account balance by account address](##45 getAccountBalanceByAddress)
	* [4.6 Get account information by account address](#46 getAccountInformationByAccountAddress)
	* [4.7 Get delegates voted by the account address](#47 getDelegatesVoteByAccountAddress)
	* [4.8 Get number of delegates](#48 getNumberofDelegates)
	* [4.9 Get delegates information with sort options](#49 getDelegateInfoSort)
	* [4.10 Get voters of delegate by delegate public key](#410 getVotersByDelegatePublicKey)
	* [4.11 Get delegate detail info. by public key](#411 getDelegateDetailbyPubKey)
	* [4.12 Get delegate detail info. by name](#412 getDelegateDetailbyName)
	* [4.13 Get/analyse block information](#413 getAnalyzeBlockInfo)
	* [4.14 Get block information by block ID](#414 getBlockInfoByID)
	* [4.15 Get block information by block height](#415 gBlockInofByHeight)
	* [4.16 Get peer/node status](#416 getPeerNodeStatus)
	* [4.17 Get unconfirmed transaction by public key](#417 getUnconfByPubKey)
	* [4.18 Get/analyse transaction information](#418 getAnalyseTransInfo)
	* [4.19 Get transaction detail information by transaction ID](#419 getTransDetailByTXID)
	* [4.20 Transfer money](#420 xferMoney)
	* [4.21 Register delegate](#421 registerDelegate)
	* [4.22 Vote for delegate](#422 voteDelegate)
	* [4.23 Cancel vote for delegate](#423 cancelVote)
	* [4.24 Set second password (secret)](#424 set2ndPass)
	* [4.25 Register Dapp (Decentralized Application)](#425 registerDAPP)
	* [4.26 Create/Delete Contract ](#426 contractOps)
	* [4.27 Create Account/Keys](#427 createAccountKeys)
	* [4.28 Create/Fund/Change Delete Dapp](#428 dappOps)
	* [4.29 Create genesis block](#429 createGenesis)
	* [4.30 Get status of all nodes/peers](#430 getStatusPeers)
	* [4.31 Get delegates' status](#431 getDelegateStatus)
	* [4.32 Get delegate location by IP address](#432 getDelegateLocation)

---
<a name="0 MCC-CLI Overview"></a>

From [MCC Whitepaper](https://github.com/MovingCloudChain/mcc-docs/blob/master/Whitepaper/MCC_whitepaper1.0.md)

### The MCC-CLI utility provides a way to interact with the MCC blockchain using a command line interface or CLI.   It provides an interface to the platform and blockchain APIs and can help developers rapidly establish a sidechain through a few simple options and configuration commands.   This guide demonstates simple command usage and parameters with additional command specific help available through the built-in help system. 

<a name="1 MCC-CLI Installation"></a>
##1 MCC-CLI Installation
- Install nodejs package manager **npm**
`sudo apt-get install npm`

- Install MCC-CLI 
`npm install -g MCC-cli`
NOTICE: if you install it in China, try parameter `--registry=http://registry.npm.taobao.org` to accelerate the installation.

<a name="2 Command Syntax"></a>
##2 MCC-CLI Syntax
`MCC-cli [option] [command]`

<a name="3 Option Description"></a>
##3 MCC-CLI Options 


<a name="31 MCC-CLI Print Help Information"></a>
###3.1 Print help information

**Parameter:** 	-h, --help  
**Return:**     Returns option specific usage and help information  
**Usage:**  	
 - MCC-cli -h #print help information of MCC-cli itself 
 - MCC-cli [commands] -h #print help information of MCC-CLI command

**Examples:**
root@MCC:~# MCC-cli -h 

Returns 

```
getheight                              get block height
getblockstatus                         get block status
openaccount [secret]                   open your account and get the infomation by secret
openaccountbypublickey [publickey]     open your account and get the infomation by publickey
getbalance [address]                   get balance by address
getaccount [address]                   get account by address
getvoteddelegates [options] [address]  get delegates voted by address
getdelegatescount                      get delegates count
getdelegates [options]                 get delegates
getvoters [publicKey]                  get voters of a delegate by public key
getdelegatebypublickey [publicKey]     get delegate by public key
getdelegatebyusername [username]       get delegate by username
getblocks [options]                    get blocks
getblockbyid [id]                      get block by id
getblockbyheight [height]              get block by height
getpeers [options]                     get peers
getunconfirmedtransactions [options]   get unconfirmed transactions
gettransactions [options]              get transactions
gettransaction [id]                    get transactions
sendmoney [options]                    send money to some address
registerdelegate [options]             register delegate
upvote [options]                       vote for delegates
downvote [options]                     cancel vote for delegates
setsecondsecret [options]              set second secret
registerdapp [options]                 register a dapp
contract [options]                     contract operations
crypto [options]                       crypto operations
dapps [options]                        manage your dapps
creategenesis [options]                create genesis block
peerstat                               analyze block height of all peers
delegatestat                           analyze delegates status
ipstat                                 analyze peer ip info

  Options:

-h, --help         output usage information
-V, --version      output the version number
-H, --host <host>  Specify the hostname or ip of the node, default: 127.0.0.1
-P, --port <port>  Specify the port of the node, default: 
-M, --main         Specify the mainnet, default: false
```


<a name="32 Print Version"></a>
###3.2 Print MCC-CLI Version Information 

**Parameter:** 	-V, --version  
**Return:**     Output the version information  
**Usage:**  `MCC-cli -V`	

**Example:**

``` 
root@MCC:~# MCC-CLI -V
>1.1.2
```
<a name="33 Set Host"></a>
###3.3 Set the host name or IP address of MCC node

**Parameter:** -H, --host &lt;host&gt; [command] *(Default: 127.0.0.1)* 

**Return:** none

**Usage:** `MCC-cli -H 45.32.248.33 [command]`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 getheight
> 101236

```
<a name="34 Set Port"></a>
###3.4 Set port number to connect to MCC target server

**Parameter:** -P, --port &lt;port&gt; [command] *(Default: 16833)*

**Return:** none

**Usage:** `MCC-cli -P 16833`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getheight  
> 102313
```
<a name="35 Set Main Chain"></a>
###3.5 Select MainNET
**Parameter:** -M, --main     *(Default: test chain)*

**Return:** none

**Usage:** `MCC-cli -M` 

**Example:**

```
# Get the block height of MCC main chain

root@MCC:~# MCC-cli -M -H *.*.*.105 -P 16833 getheight  
> 9388
```
<a name="4 MCC Supported Commands"></a>
##4 MCC-CLI Supported Commands
<a name="41 Get Block Height"></a>
###4.1 Get blockchain Height
**Command:** getheight

**Return:** blockchain height

**Usage:** `MCC-cli getheight`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getheight
105387
```
<a name="42 Blockchain Status"></a>
###4.2 Get blockchain status
**Command:** getblockstatus

**Return:** a JSON format string including blockchain height, transaction fee, milestone, the reward of each delegate's block and current volume information.

**Usage:** `MCC-cli getblockstatus`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getblockstatus
{
  "success": true,
  "height": 105392,
  "fee": 10000000,
  "milestone": 0,
  "reward": 350000000,
  "supply": 10036887200000000
}
```
<a name="43 get account info"></a>
###4.3 Get account information by password
**Command:**  openaccount [secret]

**Return:** A JSON string containing account information such as address, balance, public key, and second public key and other information.

**Usage:**`MCC-cli openaccount "password"`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 openaccount "fault still attack alley expand music basket purse later educate follow ride"
{
  "address": "16723473400748954103",
  "unconfirmedBalance": 20000000000,
  "balance": 20000000000,
  "publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",
  "unconfirmedSignature": false,
  "secondSignature": false,
  "secondPublicKey": "",
  "multisignatures": [],
  "u_multisignatures": []
}
```
<a name="44 getAccountByPublicKey"></a>
###4.4 Get account information by public key
**Command:**openaccountbypublickey [publickey]

**Return:** A JSON string containing  account information such as address, balance, public key, and second public key and other information.

**Usage:** `MCC-cli openaccountbypublickey "public key"`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 openaccountbypublickey "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"
{
  "address": "16723473400748954103",
  "unconfirmedBalance": 20000000000,
  "balance": 20000000000,
  "unconfirmedSignature": false,
  "secondSignature": false,
  "secondPublicKey": "",
  "multisignatures": [],
  "u_multisignatures": []
}
```
<a name="45 getAccountBalanceByAddress"></a>
###4.5 Get account balance by account address
**Command:** getbalance [address]

**Return:** A integer number that will be the account balance when divided by 100000000

**Usage:** `MCC-cli getbalance [account address]`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getbalance 16723473400748954103
20000000000
```
<a name="46 getAccountInformationByAccountAddress"></a>
###4.6 Get account information by account address 
**Command:** getaccount [address]

**Return:** A JSON string containing  account information such as address, balance, public key, and second public key and and other information.

**Usage:** `MCC-cli getaccount [account address]`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getaccount 16723473400748954103
{
  "address": "16723473400748954103",
  "unconfirmedBalance": 20000000000,
  "balance": 20000000000,
  "publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",
  "unconfirmedSignature": false,
  "secondSignature": false,
  "secondPublicKey": "",
  "multisignatures": [],
  "u_multisignatures": []
}
```
<a name="47 getDelegatesVoteByAccountAddress"></a>
###4.7 Get delegate votes by account address
**Command:** getvoteddelegates [options] [address]

**Return:** A list containing the delegates voted for by this account

**Usage:**`MCC-cli getvoteddelegates [account address] -o offset -l [a number indicates maximum delegates that can be printed]`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getvoteddelegates 15745540293890213312 -o 1 -l 2
{ success: true,
  delegates: 
   [ { username: 'wgl_002',
       address: '14636456069025293113',
       publicKey: 'ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7',
       vote: 8902736443247261,
       producedblocks: 1041,
       missedblocks: 6,
       rate: 1,
       approval: '88.70',
       productivity: '99.42' },
     { username: 'wgl_003',
       address: '9961157415582672274',
       publicKey: 'c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2',
       vote: 8902736443247261,
       producedblocks: 1043,
       missedblocks: 8,
       rate: 2,
       approval: '88.70',
       productivity: '99.23' }]
```
<a name="48 getNumberofDelegates"></a>
###4.8 Get the number of delegates
**Command:** getdelegatescount

**Return:** An integer number indicates the count of all delegates

**Usage:** `MCC-cli getdelegatescount`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getdelegatescount
232
```
<a name="getDelegateInfoSort"></a>
###4.9 Get list of delegates with sort options
**Command:**getdelegates [options]

**Return:** A list containing all delegates' information

**Usage:** `MCC-cli getdelegates -o [offset number] -l [a number indicates maximum delegates that can be printed] -s rate:asc` 

**NOTICE:** rate:asc means ascending sort according to votes. Get other sort types with `MCC-cli getdelegates -h`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 getdelegates -o 1 -l 1 -s rate:asc
[
  {
    "username": "wgl_003",
    "address": "9961157415582672274",
    "publicKey": "c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2",
    "vote": 9901544836887660,
    "producedblocks": 1044,
    "missedblocks": 8,
    "fees": 12150495022,
    "rewards": 161000000000,
    "rate": 2,
    "approval": 98.65,
    "productivity": 99.24,
    "forged": "173150495022"
  }
]
```
<a name="410 getVotersByDelegatePublicKey"></a>
###4.10 Get list voters of a delegate by public key
**Command:** getvoters [publicKey]

**Return:** A list containing all the voters

**Usage:** `MCC-cli getvoters "delegate's public key"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getvoters "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7"
[
  {
    "address": "2918354313445278349",
    "publicKey": "4fde4c49f1297d5d3a24b1494204543c4281aff17917ff7ff8ff32da3b4b222f",
    "balance": 1215522376203,
    "weight": 0.012110398031994424
  },
  {
    "address": "1523444724068322527",
    "publicKey": "8a6a61c28dc47541aadf1eecec2175c8f768f2331eea3472b1593bf1aa4e1fb4",
    "balance": 2109297623765,
    "weight": 0.02101519008767971
  }]
```
<a name="411 getDelegateDetailbyPubKey"></a>  
###4.11 Get detailed delegate information by public key
**Command:** getdelegatebypublickey [publicKey]

**Return:** A JSON string containing delegate's detail information such as name, address, votes, produced blocks, and forging reward and other information.

**Usage:** `MCC-cli getdelegatebypublickey "delegate's public key"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getdelegatebypublickey "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7"
{
  "username": "wgl_002",
  "address": "14636456069025293113",
  "publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7",
  "vote": 9901546586887660,
  "producedblocks": 1042,
  "missedblocks": 6,
  "fees": 12383762523,
  "rewards": 161700000000,
  "rate": 1,
  "approval": 98.65,
  "productivity": 99.43,
  "forged": "174083762523"
}
```
<a name="412 getDelegateDetailbyName"></a>
###4.12 Get detailed delegate information by name
**Command:** getdelegatebyusername [username]

**Return:** A JSON string containing delegate's detail

**Usage:** `MCC-cli getdelegatebyusername "delegate's name"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getdelegatebyusername "wgl_002"
{
  "username": "wgl_002",
  "address": "14636456069025293113",
  "publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7",
  "vote": 9901546586887660,
  "producedblocks": 1042,
  "missedblocks": 6,
  "fees": 12383762523,
  "rewards": 161700000000,
  "rate": 1,
  "approval": 98.65,
  "productivity": 99.43,
  "forged": "174083762523"
}
```
<a name="413 getAnalyzeBlockInfo"></a>
###4.13 Get/analyze block information
**Command:** getblocks [options]

**Return:** A JSON string containing query result status and queried block information

**Usage:** `MCC-cli getblocks -o [offset number] -l [an integer that indicate maximum return data] -r [reward amount] -f [fee] -a [total amount] -g [public key that generates blocks] -s [sort rule]`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getblocks -o 1 -l 1 -r 350000000
{
  "success": true,
  "blocks": [
    {
      "id": "5533619110613125681",
      "version": 0,
      "timestamp": 3914630,
      "height": 60481,
      "previousBlock": "11174102253820291084",
      "numberOfTransactions": 0,
      "totalAmount": 0,
      "totalFee": 0,
      "reward": 350000000,
      "payloadLength": 0,
      "payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
      "generatorPublicKey": "68b28341605a24f6684df81882df1b13f421ec1cbba7d9aaa68f6c079705b258",
      "generatorId": "10651956562526682705",
      "blockSignature": "77115fdaab3215039bcf2bf8b3a461b3b7cafca7adae07e271a1a953ca6531a9e93f985bbec8544d596a568595661f1da742e20797b827d5b20aa75e8d80cc0b",
      "confirmations": "45349",
      "totalForged": 350000000
    }
  ],
  "count": 45350
}
```

<a name="414 getBlockInfoByID"></a>
###4.14 Get block information by block ID
**Command:** getblockbyid [id]

**Return:** A JSON string containing block ID, block height, previous block ID, total transaction number, total amount, transaction fee, reward, hash, block generator public key and ID, block signature, quantity of confirmation and other information.

**Usage:** `MCC-cli getblockbyid [block ID]`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getblockbyid 1425942128040906871 #Get the genesis block
{
  "id": "1425942128040906871",
  "version": 0,
  "timestamp": 0,
  "height": 1,
  "previousBlock": "",
  "numberOfTransactions": 103,
  "totalAmount": 10000000000000000,
  "totalFee": 0,
  "reward": 0,
  "payloadLength": 19417,
  "payloadHash": "dd5cd3186d32145b01f8fd0bd23e3b3d72414b59b162d2e664e759db8fe60d46",
  "generatorPublicKey": "2af8566f8555bafb25df5a50e2e22b91a8577ceabc05d47dbd921572d28330e8",
  "generatorId": "1170992220085500484",
  "blockSignature": "a8ed06bfbfd1b630b1628e97a5c7c9383337c4ce32825969fad830890e0af981312be635b775ff46eea4f739da043f668a70efd5a940429e39fe5063852f4a01",
  "confirmations": "105901",
  "totalForged": 0
}
```
<a name="415 gBlockInofByHeight"></a>
###4.15 Get block information by block height
**Command:** getblockbyheight [height]

**Return:** A JSON string containing block ID, block height, previous block ID, total transaction number, total amount, transaction fee, reward, hash, block generator public key and ID, block signature, quantity of confirmation and other information.

**Usage:**`MCC-cli getblockbyheight [block height]`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getblockbyheight 1
{
  "id": "1425942128040906871",
  "version": 0,
  "timestamp": 0,
  "height": 1,
  "previousBlock": "",
  "numberOfTransactions": 103,
  "totalAmount": 10000000000000000,
  "totalFee": 0,
  "reward": 0,
  "payloadLength": 19417,
  "payloadHash": "dd5cd3186d32145b01f8fd0bd23e3b3d72414b59b162d2e664e759db8fe60d46",
  "generatorPublicKey": "2af8566f8555bafb25df5a50e2e22b91a8577ceabc05d47dbd921572d28330e8",
  "generatorId": "1170992220085500484",
  "blockSignature": "a8ed06bfbfd1b630b1628e97a5c7c9383337c4ce32825969fad830890e0af981312be635b775ff46eea4f739da043f668a70efd5a940429e39fe5063852f4a01",
  "confirmations": "105922",
  "totalForged": 0
}
```
<a name="416 getPeerNodeStatus"></a>
###4.16 Get peer/node status
**Command:** getpeers [options] 

**Return:** A list containing peer ip, port, operation system, and MCC version, and other parameters.

**Usage:** `MCC-cli getpeers -o [offset] -l [an integer that indicate maximum return data] -t [status value] -s [sort type] -v [version] -p [port number] --os [OS version]` 

**NOTICE:** For further information, try `MCC-cli getpeers -h`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getpeers -o 1 -l 2 
[
  {
    "ip": "45.32.62.184",
    "port": 16833,
    "state": 2,
    "os": "linux3.13.0-87-generic",
    "version": "1.0.0"
  },
  {
    "ip": "45.32.22.78",
    "port": 16833,
    "state": 2,
    "os": "linux3.13.0-87-generic",
    "version": "1.0.0"
  }
]
```
<a name="417 getUnconfByPubKey"></a>
###4.17 Get unconfirmed transaction by public key
**Command:** getunconfirmedtransactions [options]

**Return:** A list containing details of all transactions that are not confirmed yet

**Usage:** `MCC-cli getunconfirmedtransactions -p "sender's public key" -a [recipient's address]`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 getunconfirmedtransactions -k "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3" 
[
  {
    "type": 0,
    "timestamp": 4385190,
    "senderPublicKey": "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3",
    "signature": "98d65df3109802c707eeed706e90a907f337bddab58cb4c1fbe6ec2179aa1c85ec2903cc0cf44bf0092926829aa5a0a6ec99458f65b6ebd11f0988772e58740e",
    "recipientId": "16723473400748954103",
    "senderId": "15745540293890213312",
    "amount": 10000000000,
    "fee": 10000000,
    "signatures": [],
    "id": "17192581936339156329",
    "height": 0,
    "asset": {}
  }
]
```
<a name="418 getAnalyzeTransInfo"></a>
###4.18 Get/analyze transaction information 
**Command:** gettransactions [options]

**Return:** A list containing all selected transaction's detail information

**Usage:** MCC-cli gettransactions -b [block ID] -o [offset] -l [an integer that indicate maximum return data] 

**NOTICE:** try `MCC-cli gettransactions -h` to get the information for other parameters.

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 gettransactions -o 1 -l 2 
#Get information on the first two transactions in the blockchain' 
[
  {
    "id": "10169086766604015960",
    "height": "1",
    "blockId": "1425942128040906871",
    "type": 2,
    "timestamp": 0,
    "senderPublicKey": "991e0dda00d2c33ce68dd99471de8ebea7b58711f22a2e55236b8864c6d24c84",
    "senderId": "3331250159865474723",
    "recipientId": "",
    "amount": 0,
    "fee": 0,
    "signature": "60bf38e7a3515aeaa2cac491f7737c94087f448a862099408b90c2cf96d3fe4f709e22e6471dd4e37aca111d8573beeb7b6cff4ef451633d9aaf74ab97ce8d02",
    "signSignature": "",
    "signatures": null,
    "confirmations": "105988",
    "asset": {}
  },
  {
    "id": "10375311635154792515",
    "height": "1",
    "blockId": "1425942128040906871",
    "type": 2,
    "timestamp": 0,
    "senderPublicKey": "1674ae566c633cde3e01db8f04a02ea087081a270de2dd53e0e0b97c029106fb",
    "senderId": "9948352853509008057",
    "recipientId": "",
    "amount": 0,
    "fee": 0,
    "signature": "f09c1693cc26c4028c642cb1711cf71c2dee090a50904d1590c74d865b2f5f3ba720ed792704f5379ec9c4a20b018c5e95f325ea179236777a28cddffe8c580d",
    "signSignature": "",
    "signatures": null,
    "confirmations": "105988",
    "asset": {}
  }
]
```
<a name="419 getTransDetailByTXID"></a>
###4.19 Get transaction detail information by transaction ID
**Command:** gettransaction [id]

**Return:** A JSON string containing transaction ID, block height, block ID, time stamp, sender's public key, recipient's address, total amount, fee, signature, confirmation quantity, assets, and etc.

**Usage:** `MCC-cli gettransaction [transactionID]`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 gettransaction 17192581936339156329
{
  "id": "17192581936339156329",
  "height": "105951",
  "blockId": "15051364118100195665",
  "type": 0,
  "timestamp": 4385190,
  "senderPublicKey": "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3",
  "senderId": "15745540293890213312",
  "recipientId": "16723473400748954103",
  "amount": 10000000000,
  "fee": 10000000,
  "signature": "98d65df3109802c707eeed706e90a907f337bddab58cb4c1fbe6ec2179aa1c85ec2903cc0cf44bf0092926829aa5a0a6ec99458f65b6ebd11f0988772e58740e",
  "signSignature": "",
  "signatures": null,
  "confirmations": "17",
  "asset": {}
}
```
<a name="420 xferMoney"></a>
###4.20 Transfer money
**Command:** sendmoney [option]

**Return:** transaction result. true=success, otherwise error message

**Usage:** `MCC-cli sendmoney -e "[sender's password]" -t [recipient's address] -a [transfer amount] [-s "second password"]`

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 sendmoney -e "motion group blossom coral upper warrior pattern fragile sister misery palm admin" -t 16723473400748954103 -a 100
true
```
<a name="421 registerDelegate"></a>
###4.21 Register delegate
**Command:** registerdelegate [options]

**Return:** Registering result，ture=success, otherwise error message

**Usage:** `MCC-cli registerdelegate -e "[password]" -s "[second password]" -u "[delegate's name]"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 registerdelegate -e "fault still attack alley expand music basket purse later educate follow ride" -u "delegate_register"
true
```
<a name="422 voteDelegate"></a>
###4.22 Vote for delegate 
**Command:** upvote [options] 

**Return:** Voting result, ture=success, otherwise error message

**Usage:** `MCC-cli upvote -e "[password]" -s "[second password]" -p "delegate's public key"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 upvote -e "fault still attack alley expand music basket purse later educate follow ride" -p "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"
true
```
<a name="423 cancelVote"></a>
###4.23 Cancel vote for delegate
**Command:** downvote [options]

**Return:** Cancelling vote result, ture=success, otherwise error message

**Usage:** `MCC-cli downvote -e "[password]" -s "[second password]" -p "delegate's public key"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 downvote -e "fault still attack alley expand music basket purse later educate follow ride" -p "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"
true
```
<a name="424 set2ndPass"></a>
###4.24 Set second password (secret)
**Command:** setsecondsecret [options]

**Return:** Setting up result, ture=success, otherwise error message

**Usage:** `MCC-cli setsecondsecret -e "[password]" -s "[second password]"`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 setsecondsecret -e "fault still attack alley expand music basket purse later educate follow ride" -s "ce shi er ji mi ma"
true
```
<a name="425 registerDAPP"></a>
###4.25 Register Dapp (decentralized application)
**Command:** registerdapp [options]

**Return:**

**Usage:** `MCC-cli registerdapp -e "[password]" -s "[second password]" -f [Dapp meta file]`

**Example:**


<a name="426 contractOps"></a>
###4.26 Create/Delete contracts with the contract command
**Command:** contract [options]

**Return:** 

**Usage:**
 
 `- MCC-cli contract -a 	# create a contract`
 `- MCC-cli contract -d 	# delete a contract`

**Example:**

<a name="427 createAccountKeys"></a>
###4.27 Generate Keys/Accounts using the crypto command
**Command:** crypto [option]

**Return:** A list

**Usage:**
- MCC-cli -p # generate public key according to password
- MCC-cli -g # create one or more new account

**Example:**

```
root@MCC:~# MCC-cli -H 45.32.248.33 -P 16833 crypto -g
? Enter number of accounts to generate 1
[ { address: '16723473400748954103',
    secret: 'fault still attack alley expand music basket purse later educate follow ride',
    publicKey: 'bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9' } ]
Done
```
<a name="428 dappOps"></a>
###4.28 Dapp Operations 
**Command:** dapps [options] 

**Return:** 

**Usage:** `MCC-cli dapps -h` 

**Example:**
```
 -a, --add         add new dapp
    -c, --change      change dapp genesis block
    -d, --deposit     deposit funds to dapp
    -w, --withdrawal  withdraw funds from dapp
    -i, --install     install dapp
    -u, --uninstall   uninstall dapp
    -h, --help        output usage information
```
<a name="429 createGenesis"></a>
###4.29 Create genesis block file
**Command:** creategenesis [options]

**Return:** to create a genesis block file (genesisBlock.json) and log file (genGenesisBlock.log) in the current folder

**Usage:** `MCC-cli creategenesis`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 creategenesis 
root@MCC:~# more genesisBlock.json
{
  "version": 0,
  "totalAmount": 10000000000000000,
  "totalFee": 0,
  "reward": 0,
  "payloadHash": "baebdb59d0c19a07c2440e22c0512b4efe9794565b352375195c9e7e8a3817b0",
  "timestamp": 0,
  "numberOfTransactions": 103,
...
}
```
<a name="430 getStatusPeers"></a>
###4.30 Get the status of all nodes/peers
**Command:** peerstat

**Return:** The peer's information, containing peer IP address, port, version and block height and other information.

**Usage:** `MCC-cli peerstat`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 peerstat
45.32.248.33:16833 1.0.0 106036
45.32.62.184:16833 1.0.0 106036
45.32.19.241:16833 1.0.0 106036
```
<a name="431 getDelegateStatus"></a>
###4.31 Get delegates' status
**Command:** delegatestat

**Return:** Delegates' information, containing delegates' name, address, approval votes, productivity, the amount of generated blocks, block height, ID, and the time of last block generated and other information.

**Usage:** `MCC-cli delegatestat`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 delegatestat
name	address	rate	approval	productivity	produced	height	id	time
nayimoliuguang	3331976396377269399	93	88.36%	98.39%	1037	105618	12962348710289833740	2016/08/17 21:07:20(1 hour ago)
jack	3705405381126069457	86	88.36%	99.41%	506	105628	5876778147855073736	2016/08/17 21:09:00(1 hour ago)
node_3	12796761013870716784	81	88.36%	80.51%	814	105784	4575518649204137595	2016/08/17 21:38:10(40 mins ago)
wgl_003	9961157415582672274	2	98.65%	99.24%	1047	105852	11175724889329116017	2016/08/17 21:49:40(28 mins ago)
xihulongjing	12676662200687508271	59	88.36%	76.92%	150	105853	15273855606472618453	2016/08/17 21:49:50(28 mins ago)
liangpeili	4514546945474752928	50	88.37%	99.68%	627	105855	3771943180359756069	2016/08/17 21:50:10(28 mins ago)
MCC_tea1	8812460086240160222	4	98.58%	98.79%	1059	105857	14968719538781965695	2016/08/17 21:50:30(27 mins ago)
intmaster	7321911740133937168	97	88.36%	100%	1032	105871	6757656887343300317	2016/08/17 21:52:50(25 mins ago)
mode_6	9248745407080572308	8	88.48%	100%	1060	105873	3777454410915098884	2016/08/17 21:53:10(25 mins ago)
```
<a name="432 getDelegateLocation"></a>
###4.32 Country location of nodes/peers' IP address
**Command:** ipstat

**Return:** Country Location of each peer's IP address

**Usage:** `MCC-cli ipstat`

**Example:**

```
root@MCC:~# MCC-cli -H 101.200.162.236 -P 16833 ipstat
美国	US
美国	US
美国	US
日本	JP
中国	CN
中国	CN
中国	CN
中国	CN
中国	CN
中国	CN
```
