This is a helper to compile and deploy smart contracts through geth.

Install solc compiler.

Move `solc_helper` to somewhere in your path.
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
deploy(account, value, gas, contract, code, input=optional)
```

You can use them to deploy the contract.

```javascript
var contract = create(compiled.SimpleStorage.info.abiDefinition);
var instance = deploy(eth.coinbase, 0, 10000, contract, compiled.SimpleStorage.code,10);
var instance = deploy(eth.coinbase, 10, 10000, contract, compiled.SimpleStorage.code); // if there are no constructor parameters.
```

To call a function in the contract you can use the `callContractFunction` function

```javascript
call(account, gas, contractInstance.function, input)
```

To watch the watch an event you can use the watcher function.

```javascript
contractInstance.eventName(watcher);
```

The script will also printout the gas estimates when you try to compile.
