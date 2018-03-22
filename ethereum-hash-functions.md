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

.right-column.width-33
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
