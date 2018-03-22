# Ethereum Accounts

.left-column.width-25[
**2 Different Account Types**

*External Account*
* Originate Transactions
* Can be endpoints 

*Smart Contracts*
* Activated via External Account
* Perform stored code
* Can call more transactions
]

.right-column.width-75[
![Transactions](https://cdn-images-1.medium.com/max/1600/1*I635Y9btMh667inOhDBQ_g.png)
]

???

Ethereum has two different accounts:
* External accounts
* Smart contracts

External Accounts:
* Public/Private key-pair
* Interacts with outside world
* Starts transactions
* Holds ether and pays for gas
* Think of as users

Smart Contracts:
* Created by special transaction
* Compiled code stored immutably
* Contains rules and data
* Can call other contracts
* Can't be changed, only deleted (optional)

+++

Let's dive a little bit into the technical of Ethereum.

Ethereum is implemented using two different types of accounts, or addresses.

When you start using Ethereum, you will need an External Account,
which is a Public/Private key-pair provided by your node software or hardware wallet.

You can have as many External Accounts as you desire.
External accounts can hold Ether and are (currently) the only way to create and pay for a transaction.
Each transaction is signed by the private key associated with the external account,
which verifies the origin of the given transaction using the the corresponding public key.

An external account can create a transaction that passes through one or more Smart Contracts.
Smart Contracts are compiled EVM bytecode stored at a specific location.
You compile EVM Bytecode from a higher level language like Solidity or Viper,
and deploy that bytecode to a special address that forever assigns it to a new account.
Once bytecode is saved to a specific smart contract account by the deployment process,
it is impossible to modify that bytecode, unless the rules specifically allow it.

Smart Contracts interact with themselves and other accounts based on the code stored at their address.
They also have a datastore which holds the state associated with their address.
Each smart contract's datastore is generated locally, but a hash of the resulting state
is stored in the blockchain after each set of transactions is applied.
This shows that all states are consistent when processing the chain.
