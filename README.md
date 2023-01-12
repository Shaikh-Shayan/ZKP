## 1. Creating claim schema on PolygonID

[https://platform-test.polygonid.com/](https://platform-test.polygonid.com/)

Register your organisation on this website. Now we we can create various **claim schemas** depending on the requirement of the verification. For now there are some limitations (like we cannot issue a claim on a particular address) which will be addressed in future.

For now we have created a schema:

```jsx
Schema name: Exist
Attributes: isExist
Creation date: 11/01/2023
Schema ID: e2ffc791-282c-4377-a711-e9f0973e1468
Schema hash: ce9a99f0ef3d8d4d4d8a79a374594b29
Schema URL: https://s3.eu-west-1.amazonaws.com/polygonid-schemas/78984125-1cb1-4f5a-8807-bd6092193b93.json-ld
```

These information about claims will be used in further steps.

## Clone and install dependencies

## Deploy Smart Contracts

Steps to deploy the smart contracts of the ZK Airdrop Verifier is given [here](https://github.com/reveation-labs/ZKPexperiment/blob/master/on-chain-verification/README.md).

### Explanation:

The deployed contract address will displayed after running deply.js.

1. **Validator address** it is the already deployed smart contract by polygon which validates the mathematical proofs that we provide.

```jsx
const validatorAddress = "0xb1e86C4c687B85520eF4fd2a0d14e81970a15aFB";
```

## 4. Set Request script

## 5. ZK client
