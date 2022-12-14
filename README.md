# Smart Contract Verifier

[![Tests](https://github.com/AndreMiras/smart-contract-verifier.js/workflows/Tests/badge.svg)](https://github.com/AndreMiras/smart-contract-verifier.js/actions/workflows/tests.yml)
[![Documentation](https://github.com/AndreMiras/smart-contract-verifier.js/workflows/Documentation/badge.svg)](https://github.com/AndreMiras/smart-contract-verifier.js/actions/workflows/documentation.yml)
[![npm version](https://badge.fury.io/js/smart-contract-verifier.svg)](https://badge.fury.io/js/smart-contract-verifier)

Smart contract verification library.

Makes it possible to verify some contract code against a deployed contract address.

Originally inspired by Shawn's article:
[Verify Ethereum Contracts Using Web3.js and Solc](https://www.shawntabrizi.com/ethereum/verify-ethereum-contracts-using-web3-js-and-solc/)

# Usage example

```js
const { compileExtractCompare } = require("smart-contract-verifier");
const Web3 = require("web3");
const web3 = new Web3(
  new Web3.providers.HttpProvider(process.env.RPC_PROVIDER)
);
const solcVersion = "v0.4.16+commit.d7661dd9";
const contractName = "LinkToken";
const contractFilename = "LinkToken.sol";
const contractAddress = "0x514910771AF9Ca656af840dff83E8264EcF986CA";
// assuming the LinkToken.sol file is on the file system
const contractPath = "./" + contractFilename;
const sources = { [contractFilename]: fs.readFileSync(contractPath, "utf8") };
compileExtractCompare(
  web3,
  sources,
  solcVersion,
  contractName,
  contractFilename,
  contractAddress
).then((matching) => console.log(matching));
```
