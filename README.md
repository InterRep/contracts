<p align="center">
    <h1 align="center">
        Interep contracts
    </h1>
    <p align="center">Interep Solidity smart contracts.</p>
</p>

<p align="center">
    <a href="https://github.com/interep-project" target="_blank">
        <img src="https://img.shields.io/badge/project-Interep-blue.svg?style=flat-square">
    </a>
    <a href="https://github.com/interep-project/contracts/blob/main/LICENSE">
        <img alt="Github license" src="https://img.shields.io/github/license/interep-project/contracts.svg?style=flat-square">
    </a>
    <a href="https://github.com/interep-project/contracts/actions?query=workflow%3Atest">
        <img alt="GitHub Workflow test" src="https://img.shields.io/github/workflow/status/interep-project/contracts/test?label=test&style=flat-square&logo=github">
    </a>
    <a href="https://coveralls.io/github/interep-project/contracts">
        <img alt="Coveralls" src="https://img.shields.io/coveralls/github/interep-project/contracts?style=flat-square&logo=coveralls">
    </a>
    <a href="https://eslint.org/" target="_blank">
        <img alt="Linter eslint" src="https://img.shields.io/badge/linter-eslint-8080f2?style=flat-square&logo=eslint">
    </a>
    <a href="https://prettier.io/" target="_blank">
        <img alt="Code style prettier" src="https://img.shields.io/badge/code%20style-prettier-f8bc45?style=flat-square&logo=prettier">
    </a>
    <img alt="Repository top language" src="https://img.shields.io/github/languages/top/interep-project/contracts?style=flat-square">
</p>

<div align="center">
    <h4>
        <a href="https://docs.interep.link/contributing">
            👥 Contributing
        </a>
        <span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
        <a href="https://docs.interep.link/code-of-conduct">
            🤝 Code of conduct
        </a>
        <span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
        <a href="https://appliedzkp.org/discord">
            🗣️ Chat &amp; Support
        </a>
    </h4>
</div>

---

Please, visit our [web app](https://kovan.interep.link) or our [documentation website](https://docs.interep.link) for more details.

### Deployed contracts

|         | Kovan                                                                                          | Goerli                                                      | Arbitrum One |
| ------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ------------ |
| Interep | [0xF58D...53De](https://kovan.etherscan.io/address/0xF58D3b710cDD337df432e20a806Ad04f6CfE53De) | [0x9f44...eafb](https://goerli.etherscan.io/address/0x9f44be9F69aF1e049dCeCDb2d9296f36C49Ceafb) |              |

---

## Install

Clone this repository and install the dependencies:

```bash
git clone https://github.com/interep-project/contracts.git
cd contracts
yarn # or `npm i`
```

## Usage

Copy the `.env.example` file and rename it `.env`.

### Compile

Compile the smart contracts with Hardhat:

```bash
yarn compile
```

### Lint

Lint the Solidity or the TypeScript code:

```bash
yarn lint:sol
yarn lint:ts
# or yarn lint to lint both.
```

And check if the code is well formatted:

```bash
yarn prettier
```

### Test

Run the Mocha tests:

```bash
yarn test
```

### Coverage

Generate the code coverage report:

```bash
yarn test:coverage
```

### Report Gas

See the gas usage per unit test and average gas per method call:

```bash
yarn test:report-gas
```

### Deploy

Deploy a Semaphore verifier contract with depth = 20:

```bash
yarn deploy:verifier # The resulting address will have to be used in the next step.
```

Deploy the Interep contract with one Semaphore verifier:

```bash
yarn deploy:interep --verifiers '[{"merkleTreeDepth": 20, "contractAddress": "0x06bcD633988c1CE7Bd134DbE2C12119b6f3E4bD1"}]'
```

If you want to deploy contracts in a specific network you can set up the `DEFAULT_NETWORK` variable in your `.env` file with the name of one of our supported networks (hardhat, localhost, goerli, kovan, arbitrum). Or you can specify it as option:

```bash
yarn deploy:interep --verifiers '[{"merkleTreeDepth": 20, "contractAddress": "0x5FbDB2315678afecb367f032d93F642f64180aa3"}]' --network kovan
yarn deploy:interep --verifiers '[{"merkleTreeDepth": 20, "contractAddress": "0x06bcD633988c1CE7Bd134DbE2C12119b6f3E4bD1"}]' --network localhost
```

If you want to deploy the contracts on Goerli, Kovan or Arbitrum remember to provide a valid private key and an Infura API in your `.env` file.

### Preparing a local network

Run a Hardhat Network in a stand-alone fashion:

```bash
yarn start
```

Deploy Semaphore verifier and Interep contract:

```bash
yarn deploy --network localhost
```

You can omit `--network localhost` if your `DEFAULT_NETWORK` env variable is equal to `localhost`.
