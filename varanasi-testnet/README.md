# Varanasi Testnet Repository

This repository contains essential files for the Junction v0.3.1 Varanasi Testnet, including validator gentxs and network genesis configuration.

## Directory Structure

### `/gentxs`

This directory contains the genesis transactions (gentxs) submitted by validators who joined the Varanasi testnet at genesis. Each gentx file represents a validator's commitment to participate in the network from block 1.

- Gentx files follow the naming convention `gentx-<node-id>.json`
- Each file contains the validator's configuration including moniker, commission rates, and public keys
- These files were used to construct the final genesis file for network launch

### `/genesis`

This directory contains the official genesis file (`genesis.json`) for the Varanasi testnet. This file:

- Defines the initial state of the blockchain at block height 1
- Includes all validators who submitted gentxs before the deadline
- Configures essential network parameters such as:
  - Chain ID: `varanasi-1`
  - Genesis time: March 22, 2025, 12:00:00 UTC
  - Initial token distribution
  - Module parameters for governance, staking, etc.

## Joining the Network

To join the Varanasi testnet as a validator:

1. Install `junctiond` v0.3.1 from the [official releases](https://github.com/airchains-network/junction/releases)
2. Initialize your node with `junctiond init <your-moniker> --chain-id varanasi-1 --default-denom uamf`
3. Download the genesis file from this repository
4. Configure your node and start it with `junctiond start`

For complete instructions, see the [Validator Guide](./gentxs/README.md).

## Additional Resources

- [Junction GitHub Repository](https://github.com/airchains-network/junction)
- [Official Documentation](https://docs.airchains.io)
