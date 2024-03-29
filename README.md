# Sample Hardhat Project

This project demonstrates a basic Hardhat use case. It comes with a contract generated by [OpenZeppelin Wizard](https://wizard.openzeppelin.com/), a test for that contract, and a script that deploys that contract.

## Installing dependencies

```
npm install
```

## Testing the contract

```
npm test
```

## Dev
Start local chain: 
```
npx hardhat node
```

Deploy the contract locally:

```
npx hardhat run --network localhost scripts/deploy.ts

```
Note down the address of `Proxy deployed to 0x...`
Access console: 
```
npx hardhat console --network localhost
```

Create Token: 
```
const BC24 = await ethers.getContractFactory("BC24");
const bc = await BC24.attach("0x8A791620dd6260079BF849Dc5567aDC3F2FdC318");
await bc.createToken("0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266",'{"placeOfOrigin":"Zurich", "gender":"male", "weight":300, "healthInformation":"healthy", "creationDate":"01-01-2024"}')
```
This will give you a tokenid

Inspect token:

```
await bc.getMetadata(<id>)
```

Set meta data:
```
await bc.setMetadata(<id>, {"placeOfOrigin":"Paris", "gender":"female", "weight":400, "healthInformation":"healthy", "creationDate":"01-01-2024"}' )
```

Delete token:

```
await bc.destroyToken(<id>)
```