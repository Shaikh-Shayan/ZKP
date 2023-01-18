## Creating claim schema on PolygonID

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

```jsx
git clone git@github.com:reveation-labs/ZKPexperiment.git
cd ZKPexperiment
npm install
```

## Deploy Smart Contracts

Steps to deploy the smart contracts of the ZK Airdrop Verifier is given [here](https://github.com/reveation-labs/ZKPexperiment/blob/master/on-chain-verification/README.md).

### Explanation:

The deployed contract address will displayed after running deply.js.

1. **Validator address** it is the already deployed smart contract by polygon which validates the mathematical proofs that we provide.

```jsx
const validatorAddress = "0xb1e86C4c687B85520eF4fd2a0d14e81970a15aFB";
```

## Set Request script

Run set-request to send the zk request to the smart contract:

```jsx
npx hardhat run --network mumbai scripts/set-request.js
```

This command will help set the query to the validator

```jsx
const circuitId = "credentialAtomicQuerySig";

/*
	This is the already deployed contract that will validate the claim query according to the protocol.
	*/
const validatorAddress = "0xb1e86C4c687B85520eF4fd2a0d14e81970a15aFB";

/*
	Extracted from PolygonID platform after creating the claim.
	*/
const schemaHash = "ce9a99f0ef3d8d4d4d8a79a374594b29";
const schemaEnd = fromLittleEndian(hexToBytes(schemaHash));
const query = {
  schema: ethers.BigNumber.from(schemaEnd),

  //todo:
  slotIndex: 2,

  // see - https://0xpolygonid.github.io/tutorials/verifier/verification-library/zk-query-language/
  // 1 = equals
  // 2 = less-than
  // 3 = greater-than
  // 4 = in
  // 5 = not-in
  operator: 1,

  // Change to 0 or value that you want to use.
  value: [0, ...new Array(63).fill(0).map((i) => 0)],
  circuitId,
};

// add the address of the contract just deployed
ERC20VerifierAddress = "0xE38993E35c60DD12799815691403E558E5E8Cfb1";
```

## ZK client
