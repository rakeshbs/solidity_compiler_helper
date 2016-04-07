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

Paste this statement into the geth console. Your code will be loaded and your contract will be deployed automatically.

There are also a few helper functions to easily deploy the contracts.

```javascript
create(abiDefinition)
deploy(contract, input, account, code, gas)
```

You can use them to deploy the contract.

```javascript
var contract = create(compiled.SimpleStorage.info.abiDefinition);
var instance = deploy(contract, 10, eth.coinbase, compiled.SimpleStorage.code,10000);
```

To call a function in the contract you can use the `callContractFunction` function

```javascript
call(account, gas, contractInstance.function, input)
```

To watch the watch an event you can use the watcher function.

```javascript
contractInstance.eventName(watcher);
```
