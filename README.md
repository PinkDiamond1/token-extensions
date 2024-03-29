# token-extensions

This library provides you with Solidity contract utilities to help you create a Copper NFT drop powered by Balancer's Liquidity Bootstrapping Pools.

## Installation

To get started, install the library in your NFT smart contract's project using

```shell
npm install --save @alchemist.wtf/token-extensions
```

## Extending you NFT contract

First, your NFT project must have an [OpenZeppelin ERC721](https://docs.openzeppelin.com/contracts/4.x/) compliant contract (ERC1155 support coming soon).

Once the `token-extensions` library is installed in your NFT project, you need to make the following changes to your contract:

1) Make your ERC721 contract extend the interface from `@alchemistcoin/token-extensions/contracts/Erc721BurningErc20OnMint.sol`.
2) Implement a `mint` function (as per the [IErc721BurningErc20OnMint](contracts/IErc721BurningErc20OnMint.sol) in your NFT contract that returns the token ID which is minted when that function is called

See [TestERC721.sol](contracts/test/TestERC721.sol) for a reference implementation.

## Contract unit tests

You can run solidity contract unit tests (powered by hardhat) using

```shell
npm test
```

## Deploy test contract on chain

You can deploy to an Ethereum network that's supported by Etherscan, such as Goerli.

In this project, copy the .env.example file to a file named .env, and then edit it to fill in the details. Enter your Etherscan API key, Infura project ID, and the private key of the account which will send the deployment transaction. With a valid .env file in place, first deploy your contract:

```shell
hardhat run --network goerli scripts/TestERC721/deploy.ts 
```

## Etherscan verification

Then, copy the deployment address and paste it in to replace `DEPLOYED_CONTRACT_ADDRESS` in this command:

```shell
npx hardhat verify --network goerli DEPLOYED_CONTRACT_ADDRESS
```

## Other useful dev commands

```shell
npx hardhat accounts
npx hardhat compile
npx hardhat clean
npx hardhat test
npx hardhat node
npx hardhat help
REPORT_GAS=true npx hardhat test
npx hardhat coverage
npx hardhat run scripts/deploy.ts
TS_NODE_FILES=true npx ts-node scripts/deploy.ts
npx eslint '**/*.{js,ts}'
npx eslint '**/*.{js,ts}' --fix
npx prettier '**/*.{json,sol,md}' --check
npx prettier '**/*.{json,sol,md}' --write
npx solhint 'contracts/**/*.sol'
npx solhint 'contracts/**/*.sol' --fix
```
