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
    * Fast to compute
    * Infeasible to invert
* Collision-resistant

*Ethereum uses the Keccak-256 Hash function!*
]

.right-column.width-33[
<br>

![Collision](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Hash_table_4_1_1_0_0_1_0_LL.svg/300px-Hash_table_4_1_1_0_0_1_0_LL.svg.png)

![No Collision](https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Hash_table_4_1_1_0_0_0_0_LL.svg/300px-Hash_table_4_1_1_0_0_0_0_LL.svg.png)

]
