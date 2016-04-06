This is a helper to compile and deploy smart contracts through geth.

Start geth with following flags (along with the others you may need). You can change the rpcport to any port number. Just remember to change that in the script.

`geth --rpc --rpcport 8100 --rpccorsdomain "*"`

Then move `solc_helper` to somewhere in your path.
To compile your code run

`solc_helper contract.sol`

This will generate a javascript file and print out a statement like the following.

```javascript
loadScript('/path/contract.js')
```

Paste this statement into the geth console. Your code will be loaded.

There are also a few helper functions to easily deploy the contracts.

```javascript
createContract(abiDefinition)
getContractInstance(contract, input, account, code, gas)
```

You can use them to deploy the contract.

```javascript
var contract = createContract(compiled.SimpleStorage.info.abiDefinition);
var instance = getContractInstance(contract, 10, eth.coinbase, compiled.SimpleStorage.code,10000);
```
