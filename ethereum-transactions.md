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
