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
