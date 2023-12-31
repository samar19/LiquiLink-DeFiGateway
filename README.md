
# LiquiLink-DeFiGateway - Frontend

## Access Exclusive DeFi Vaults Seamlessly on Layer 2

Welcome to the LiquiLink-DeFiGateway project's frontend. This platform enables Layer 2 (L2) users to access a curated selection of DeFi vaults that were previously only available on Ethereum Layer 1 (L1), all while bypassing the substantial gas fees associated with L1 transactions.

## Problem

The brainchild of our team member, Florent, emerged when facing exorbitant transaction costs on Ethereum L1 while attempting to engage with an innovative protocol designed for lending USDC to bond-collateralized borrowers. A pressing question arose: "How can we access these L1-exclusive vaults without incurring prohibitive gas fees?"

## Solution

The LiquiLink-DeFiGateway was born from this query. In its current incarnation, designed for the Hackathon and subject to time constraints, this platform empowers users to deposit Axelar version of USDC into a Polygon Mumbai Smart Contract called `DeFiGatewayL2`. With each deposit, a nominal fee is collected and directed to a "Fee Bucket." Rewards from this Fee Bucket are allocated to those who invoke the `DeFiGatewayL2.launchBus()` function, fostering a protocol that operates with minimal centralization. At its core, the concept involves a trade of time for financial gain, granting users access to L1 protocols while transacting on L2 and incurring L2 fees.

## Challenge

The pivotal challenge was to engineer a seamless bridge between L2 and L1, facilitating the movement of assets and ensuring the incentives for participants to make the roundtrip.

## Milestones

- Implementation of a **Chainlink Automation** smart contract with customized logic, ensuring bus launch on L1 if stuck for over 5 minutes.
- Leveraging **OpenZeppelin Defender** to automate `launchBus()` on L2 after 10,000 USDC deposited.
- Integration of React with wagmi & Tailwind for the frontend and utilizing **Tenderly Web3 Gateway** & **Alchemy** for the nodes.
- Deployment on Ethereum Goerli (DeFiGatewayL1 & GateL1) and Polygon Mumbai (DeFiGatewayL2 & GateL2).

## How It Works

1. Users deposit Axelar USDC into `DeFiGatewayL2`.
2. A small fee is collected and stored in the "Fee Bucket".
3. Invoking `DeFiGatewayL2.launchBus()` triggers rewards distribution and initiates the bridge.
4. Deposited funds bridge to Ethereum Goerli via Axelar, arriving in `DeFiGatewayL1`.
5. L1 protocol mints yield-bearing tokens (Compound, Yearn, Flux Finance) sent to `DeFiGatewayL1`.
6. Equivalent tokens are minted on L2 for bus participants, bridging L1-L2.
7. A fraction of the Fee Bucket incentivizes the bridge operator for the roundtrip.
8. L2 depositors receive a receipt token (1:1 to L1) for fund retrieval.
9. Each bus roundtrip seamlessly manages deposits & withdrawals.

## Roadmap

- Implement Chainlink Functions to monitor L1 gas prices and offer on-chain warnings for bus initiators.
- Integration with native Scroll and Base bridges.
- Creation of an Automated Market Maker (AMM) on L2 for easy position entry and exit.

## Usage

1. Clone the repository.
2. Create a `.env` file with:

```
REACT_APP_ALCHEMY_KEY=<alchemy key>
REACT_APP_COVALENT_API=<covalent key>
```

3. Install dependencies: `yarn install`
4. Start the app: `yarn start`

## Deployments

- **Ethereum Goerli**
  - DeFiGatewayL1: 0x2424e8421959f7e522afded0d607e60b30f6332d
  - GateL1: 0xb5949e4f80fbd364661c28f4fe3e0bac277706d9

- **Polygon Mumbai**
  - DeFiGatewayL2: 0xdf004020f283b46c40ee67917d8e9468c5c652e4
  - GateL2: 0x935952478e46ea2cc65c87a9187d3d2f3dd05c24

- **Base Goerli**
  - DeFiGatewayL2: 0x2B4446406Cf12aE8D5dc4E14Edd1fc06cE6f9815
  - GateL2 (WIP): 0x014Cc34DfFe4Ed166E8Cd2f6f78fFDAF0bdEba62

- **Scroll Alpha**
  - DeFiGatewayL2: 0x8d7F472B95410F2e18A4348802a79e4d2ed76398
  - GateL2: 0xf584d6b98aE9cA1dAD0d0b17422beEeF8745C1E7

We've deployed DeFiGatewayL2 on Scroll and Base (without GateL2) due to bridge limitations.

## Plan your retirement

Use DeFi Vaults to explore investments for retirement planning. The frontend helps estimate required deposits to achieve your goals.

