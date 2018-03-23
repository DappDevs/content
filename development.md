background-image: url(http://ak6.picdn.net/shutterstock/videos/28681036/thumb/10.jpg)
class: middle, center, green, shadow

# **Shill-a-Coin Workshop**

**NO COINS WERE HARMED IN THE MAKING OF THIS WORKSHOP**

???

Who's ready to Shill some coins???

---

# Client node (MetaMask)
* Download MetaMask extension for Chrome (or the Brave browser)
* Create a new encrypted DEN with your password
    * A DEN is an encrypted private key store only accessible on your device!
    * **NOTE**: All networks use the same address **DO NOT FORGET THIS**
* Unlock your DEN

.center[![MetaMask](https://metamask.io/img/ethereum-metamask-chrome.png)]

???

Walk through MetaMask install

Have them put their MetaMask addresses in the spreadsheet

---

# Give me ETH!

.left-column.width-50[

* Visit Rinkeby Faucet at [faucet.rinkeby.io](https://faucet.rinkeby.io/)
* Create a public social media post with your MetaMask address
* Share the URL and ask for 18.75 Ethers

*NOTE*: If you don't have social media, we can supply you *some* Rinkeby ETH

]

.right-column.width-50[

![Testnets](https://cdn.ethnews.com/images/1024x512/ethereums-new-testnet-1024x512-03-08-2017.jpg)

]

???

Walk through testnets and faucets

---

# Play with Remix

.left-column.width-66[
* Go to [remix.ethereum.org](https://remix.ethereum.org)
* Download 'DappDevsToken.sol' from 
[github.com/DappDevs/token](https://github.com/DappDevs/token/blob/master/contracts/DappDevToken.sol)
* Upload it to remix
* Deploy a token with your Rinkeby address
* Give some to your peers!
]

.right-column.width-33[
![Remix](https://cdn-images-1.medium.com/max/256/1*oKbTW12Lakv6Iwfz19vySw.png)
]

???

Walk through remix

Let them play for a bit...

Have them put their token addresses in the spreadsheet

---

# Let's shill some coins!

.left-column.width-66[
Develop an ICO smart contract that earns you the most ShillTokens

Rules:
* There are no rules, winner takes all!
* Yes, you can talk or strategize with others
* Yes, you can exploit other's smart contracts
* Yes, you can ask for help!
* Yes, this is pure, unadulterated capitalism

Suggestions:
* Think about incentivization
* Be transparent (transparency ==> trust ==> users)
* Be nice! (see above)
* Market your ICO! (No one said you can't)
]

.right-column.width-33[
![Shill Coins](http://www.coincalendar.info/wp-content/uploads/2018/01/Banner.png)
*I mean, you could be this guy ^ ...*
]

???

Discuss what the challenge is

Ask for questions

---

# Ready to Rumble!
.left-column.width-66[
* Download the 'SampleICO.sol' contract from [github.com/DappDevs/coin-workshop](https://github.com/DappDevs/coin-workshop/blob/master/contracts/SampleICO.sol)
* Upload it to remix
    * Use the Javascript VM instead of Rinkeby
* Make sure to throughly test your modifications
* Make sure it works with the ICO interface, and with the ERC20 interface
    * Or not... no one says you have to!

You have 30 mins, then we will deploy as a group... GO!
]

.right-column.width-33[
![Coder](https://media.giphy.com/media/ZVik7pBtu9dNS/giphy.gif)
*Time to get down to business!*
]

???

Set an alarm, and go around the room

Deploy and Publish Token contract to Rinkeby

---

# Deploy!
.left-column.width-66[
* Make sure to deploy to Rinkeby
* Log the `RegisterICO(token_address)` event
    * So we know the location of your contract
* Make sure to fund your ICOs with both Tokens and Ether
    * Otherwise people can't interact with it
* You are allowed to talk
    * But don't yell... or be mean
* Your neighbors are tricky!
    * Watch out for exploits or scams!

You will have 20 mins to get as many Tokens as possible... GO!

\*NOTE: First MetaMask address to get 90% of the tokens wins by default

]

.right-column.width-33[
![Hungry Hippos](https://media.giphy.com/media/Fwn1auHR2LUGI/giphy.gif)
]

???

Alarm went off, pencils down!

Facilitate address sharing somehow...

Discuss what to do next...

GO!

---

# Winner Winner Chicken Dinner!
.left-column.width-66[
* Navigate to [rinkeby.etherscan.io/token/[token_address]]()
* Whoever has the most tokens wins!

# Debrief
* What issues did people have
* Any bugs, locked tokens, locked funds?
* What worked technically? Socially?
* Did anyone hack another ICO? The token contract?
]

.right-column.width-33[
![Winner Winner](https://i.ebayimg.com/images/g/UfAAAOSwal5YD4Rs/s-l300.jpg)
]

???

Figure out winner based on Token contract on Etherscan

Ask if anyone had problems, questions, etc.

When things wrap up, let everyone network for a bit and decompress
