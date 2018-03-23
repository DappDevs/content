# Building the Ethereum Blockchain

.left-column.width-33[
Core Concepts:
* Cryptograhpic Hash Functions
* Public Key Cryptography
* Accounts
* Transactions

Transactions &rarr; Blocks &rarr; Chains

It's actually kinda boring...

But VERY difficult to get right!

So, don't roll your own!
]

.right-column.width-66.center[
![ethereum blockchain](https://www.financemagnates.com/wp-content/uploads/2015/07/Ethereum.png)
*This is what the Ethereum blockchain actually looks like... Just kidding!*
]

???

Walk-through technologies that enable blockchains like Ethereum

Basically Accounts:
* have attributes (like Crypto holdings)
* and use Public Key Cryptography
* to submit transactions originating from key holders

Transactions go into blocks

Blocks are chained together

Boom, you have a blockchain!

It's really that simple.

The hard part is doing it securely.

But first, let's learn more about the tech.

---

.left-column.width-66[
# All About Hash Functions

How a Cryptographic Hash works:
* Arbitrary amount of bytes as input
* Psuedo-random calculation on input
* Produces a fixed size output
    * aka "digital fingerprint"

Properties of a Cryptographic Hash:
* Deterministic (input ==> output)
* "One-Way" function
    * Relatively fast to compute
    * Infeasible to invert
* Collision-resistant

*Ethereum uses the Keccak-256 Hash function!*
]

.right-column.width-33[
<br>

![Collision](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Hash_table_4_1_1_0_0_1_0_LL.svg/300px-Hash_table_4_1_1_0_0_1_0_LL.svg.png)

![No Collision](https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Hash_table_4_1_1_0_0_0_0_LL.svg/300px-Hash_table_4_1_1_0_0_0_0_LL.svg.png)

]

???

Hashing functions are a class of functions
* Arbitrary input ==> fixed-length output
* Akin to a "Digital Fingerprint"

Output is psuedo-random
* Slightly different inputs ==> uncorrelated outputs
    * This is "collision resistance"

Psuedo-random means deterministic
* Same input ==> same result

One directional
* quick to compute
* difficult to reverse

Used for many things in blockchains
* maintains chain-like structure in blockchain
    * 6 block confirmations
* data storage
    * Python `dicts` vs Ethereum `mappings`
* betting and auctions
    * Pre-commit (proof of integrity)

+++

The hash function is a very special class of functions with special properties.
The concept of their use is as follows: given an arbitrary amount of bytes containing
any kind of data, take that input and compute a standard-sized output (often 32 bytes),
using psuedo-random number generation to produce vastly different results for similar inputs.
A good way to think about this is as a sort of "Digital Fingerprint" for a piece of data.

This fingerprint is useful for determining the integrity of a given set of data. Since it
is deterministic, which means the same output is always generated for a given input, and one-
directional, meaning there is no way to feasibly compute a specific input that produces a
desired output, it lends a high degree of certainity that a given piece of data is unmodified.
All you have to do to verify this is do it yourself! Run that same piece of data through the
same algorithm, and you should get the same result, no matter what happens. This ability to
easily self-verify the integrity of data is what makes it so powerful.

One important thing property that cryptographic hash functions typically have is this idea
of "collision resistance", or that a given input is equally likely to compute any one of a
number of outputs, so that no one output is used more than it has to be.
This is very important because a hashing function that favors a specific output over others
is very likely to be exploited in order to convince others a different set of data is correct.
Cryptographic hashing functions actually have a proof that the liklihood of a collision is
below a minimal threshold where it is not feasible to use it as an attack vector, hence why
"cryptographic" is in it's name. Non-cryptographic hash functions do exist and are commonly
used for purposes where security is not a big concern, typically when speed or efficiency is
the driving factor.

A great example is the `dict` data structure in Python. It uses a non-cryptographic hash
table to store key-value data sets in memory, and can be broken when large data sets are used.
Ethereum has a similar data structure called a `mapping`, but since it can potentially store
very large amounts of data and is likely to be attacked, a cryptographic hash function was
chosen for this purpose.

Hash functions are probably one of the powerful things that enables "blockchain technology".
How the blocks are "chained" together is basically the hash function, as it is impossible
to modify a hash in a given block without breaking the hash computation of the next one.
Since anyone can easily verify the chain of blocks each has the correct hash, and the fact
that it is nearly impossible to find a different set of transactions that will compute the
same hash, someone who wanted to modify a transaction in the middle of the blockchain would
have to propagate the updated hash from each block that came after it in time.

This has a practical effect, this is actually how block confirmations occur. In Bitcoin
and other public blockchains, a transaction is considered fully "confirmed" if it is at least
6 blocks deep. At that level, it is extremely unlikely that someone was able to publish an
alternative history from that depth and get the network to accept that history as truth.
That number is extremely conservative, overkill for many casual users, but represents a real
possibility where there is a non-negliable chance of success for an attacker with more than 10%
of the mining power.

All that aside, the hashing function is a very important concept to understand for it's applications
in securing the blockchain.

---

# Public Key Cryptography

.left-column.width-66[

*A story of two keys*

2 randomized string of bytes
* Must satisfy a mathematically relationship
* Infeasible to compute one given the other
* Not the same size

1-way relationship
* Encrypted w/ Private ==> Decrypted w/ Public
* Encrypted w/ Public ==> Decrypted w/ Private

Not impossible to compute, just *hard*
* 10^18 years to brute force relationship
* Quantum computing may do it quicker

]

.right-column.width-33[

![PK Messaging](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Public_key_encryption.svg/525px-Public_key_encryption.svg.png)

]
???

Public Key Cryptography is not an algorithm, but a concept
* 2 numbers with a special relationship
* Can't compute one given the other

Used in 2 "directions":
1. Authentication or Non-repudiation
    * conclusive "proof" that you sent a message
    * also called a  *Digital Signature*
2. Encryption
    * only private key holder can "unlock" message
    * *Slotted Mailbox*

Cryptocurrencies use first relationship
* Public ledger, private keys
* Key holders send transactions by proving they are owners of accounts that hold valuable assets

Quantum computing a risk, but public key algorithms are basically interchangeable

+++

Public key cryptography is the underpinning for the vast majority of encryption schemes in use today,
including the schemes which blockchains use to securely manage their state.

It is a family of algorithms that use the same concept for their design and have the same goals.
There are two keys, which are not the same, that have a special relationship to each other.
If you encrypt a message using one of the keys, then the other key is the only one that can
decrypt the message and return the original.

The Private key is, well, private. It is typically larger than it's counter part in order
to guarentee that it will take much longer to brute force than is feasible.
The other key is publicly shared, everyone knows what it is and they can use it in relationship
with messages they wish to communicate to the holder of the private key.

Their one way relationship, and the fact that one is secret and the other is widely distributed,
guarentees an asymetry of information exists that can be exploited to communicate privately with
a given party over an insecure channel.

Depending on the direction of this asymmetry, it can be used in two seperate ways:
If the data is encrypted using the private key, since the public key is the only one that
can decrypt it, this is how we show that the sender of that encrypted data is in possession
of the private key.

This is how Crypto leverages Public Key Cryptography, basically proving that a transaction
is authorized by the owner of that private key when it is broadcasted to the network.
A good way to picture this is that the sender is holding a unique pen with special ink
that cannot be manufactured and they "signed" the message with this pen, showing that the message
is forever attributable to the owner of that private key.

The other direction is when someone has a message they want to send another person.
They will encrypt using the public key and send it over an insecure medium to the receiver,
who holds the private key, and is the only one who can decrypt this message.
This is how most authentication schemes work, using this relationship to trade secrets
and establish a secure channel with another party of an insecure medium

Public Key Cryptography is state of the art and heavily battletested, but that is not to
say it is fool proof. All implementations operate using the fact that a computing the
relationship between the public and private key is computationally infeasible. For Bitcoin,
computing a private key from the corresponding public key and a single message signed
by that private key would take the most powerful super computer (which is the Bitcoin network,
ironically) about 1 billion billion years, a number far larger than the lifespan of the universe.

Certain implementations have been cracked however, as the underlying shortcuts the designers
of the algorithm take often prove to have fatal flaws that allow them to be computed much, much
faster, on the order of years, months, days or (rarely) hours.
The spectre of Quantum Computing has many cryptographers worried, as it enables certain kinds
of brute force computations to be vastly more efficient to calculate, meaning brute forcing of
many types of cryptographic algorithms may become nearly trivial to break. They are also worried
because quantum computing will enable new kinds of algorithms yet to be discovered that could
also allow most algorithms to be broken give time and ingenuity. Researchers are actively working
quantum-resistant algorithms that could be used to counter this effect, but only time will tell
just how dangerous (and expensive!) these attacks might be.

It's constantly a cat and mouse game with cryptography, that's why the designers of Ethereum
decided not to hardcode the encryption algorithm used in the protocol. Since all public key
encryption algorithms share the same uses cases and interfaces, these implementations can be
easily swapped for a more resistant one at a later date.

---

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

---

# Anatomy of an Ethereum Transaction

.left-column.width-25[
**Steps:**
* Signed by *External Account* (private key)
* Provides starting gas and gas price
* Gas is charged for each instruction used
* The remaining gas is refunded
* The transaction is mined into a block
]

.right-column.width-75[
![EVM](https://cdn-images-1.medium.com/max/800/1*UNCaS12SsPln7DEnRvcONQ.png)
]

???

Transaction process
* Generate call data (function sig + arguments)
* Specify receiver, gas limit and price
* Sign call with external account (Private key)
* Broadcast to the network
* Miner executes transaction
* Ether is moved and/or functions are executed
* Each instruction in function incurs gas cost
* Calls continue until complete
* Gas is totalled, multiplied by price
* Fee is deducted
* State is computed and put into block
* Transaction is put into block
* Miner mines block when it solves PoW puzzle

Transaction is confirmed on the blockchain!

+++

A bit more of a detailed walk-through of how a transaction works.

First, the client generates a set of data corresponding to the transaction,
such as the destination, how much value to send, and some other parameters.
Then that transaction is signed by the private key associated with the sender's account.

Next, the client provides an amount of gas to pay for the transaction and broadcasts it
to the entire Ethereum network.

A miner listening on the network will hear this broadcasted transaction and,
based on the gas price being paid and the gas limit stated,
they will begin processing that transaction for inclusion into the block they are mining.

For the first destination of the transaction, any Ether is transferred and any
code available at the destination gets executed according the data provided.
If the call matches a function definition, it will execute that function with the given
parameters, recording each instruction and how much gas it uses.

If the function contains another function call, this cycle repeats and
the call will forward to the appropriate contract's function and additional gas will be used.
When the call completes, the total gas usage is recorded, multiplied by the gas price,
and the resulting fee is debited from the sender and credited to the miner.

That processed transaction is then committed to the ledger (including a hash of the corresponding
state post-execution), and mined along with several other transactions into a block.

Every miner on the network is attempting to convince the others that they have the latest block.
The first one to solve the PoW puzzle will get their block accepted, and they will receive
the block reward and any fees from the transactions they process.

The transaction is now on the blockchain!
