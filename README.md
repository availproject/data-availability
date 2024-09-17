<div align="Center">
<h1>Avail</h1>
<h3>Documentation & Links for the Avail blockchain</h3>
</div>

<br>

Avail is a data availability focused blockchain. Here is a list of GitHub repo tracking the various development efforts in this regard. 

|    Name (with link)    |                                       Description                                       |
|:----------------------:|:---------------------------------------------------------------------------------------:|
| [Reference Document](https://github.com/availproject/data-availability/blob/master/reference%20document/Avail%20Reference%20Paper%20v2%2017%20Sept%202024.pdf)     | Document containing the overall rationale, design decisions and theoretical backgrounds                              |
| [Avail Node](https://github.com/availproject/avail)                             | Avail node implementation repo. Built using Substrate.              |
| [Light Client](https://github.com/availproject/avail-light)                     | Light client designed to check data availability proofs on Avail.   |
| [Explorer](https://github.com/availproject/avail-apps)                                | Avail explorer implementation repo. Built using Polkadot apps.      |
| [Bridge UI](https://github.com/availproject/bridge-ui)                                | Repository for the official Avail <-> ETH bridge UI      |
| [Documentation](https://availproject.github.io/) | Avail documentation hub.                                    |
| [Tests](https://github.com/availproject/avail-test)                             | End to end tests for Avail.                                         |

Suggestions and feedback welcome.

## Avail Architecture

There are two main components in the Avail network:

- [Avail Node](https://github.com/availproject/avail): This forms the blockchain layer of Avail. It is built using Substrate, with modifications to specialize it for data availability. Apart from basic blockchain operations like balance transfer, validator staking, slashing and governance, it also contains methods for applications to submit data blobs. This network is secured by the GRANDPA+BABE consensus engine, under the assumption that at least 2/3 of the validator set is honest.
- [Avail Light Client](https://github.com/availproject/avail-light): The light clients (LC) form an overlay P2P network. Individually, all LCs subscribe to (finalized) headers of the chain. It performs Data Availability Sampling (DAS) to gain high confidence of DA. The LCs also host the sampled data on the P2P so that together the P2P network can have the entire data in a highly available manner.

![Avail Architecture](./images/Light%20Client%20P2P%20Network.jpg)

## Data Attestation Bridge

To enable Validium constructions based on Ethereum, it is important to push data roots from Avail to Ethereum. We partner with [Nomad](https://www.nomad.xyz/) for building the data attestation bridge. Overall, the architecture looks like as follows:

