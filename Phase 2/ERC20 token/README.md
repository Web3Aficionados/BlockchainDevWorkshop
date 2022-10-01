# Build your first ERC20 token

In this class, you will learn how to build and deploy an ERC-20 token on Ethereum test network.

We will use Metamask and Remix IDE for this tutorial.

## What is ERC-20?

ERC stands for Ethereum Request for Comment.

ERC-20 is the technical standard for fungible tokens created using the Ethereum blockchain. A fungible token is one that is interchangeable with another token—where the well-known non-fungible tokens (NFTs) are not interchangeable.

ERC-20 allows different smart-contract enabled tokens a way to be exchanged. Tokens, in this regard, are a representation of an asset, right, ownership, access, cryptocurrency, or anything else that is not unique in and of itself but can be transferred. The standard allows tokens representing one of these factors—along with smart contracts—to be exchanged for a token that represents another. Smart contracts are conditions written into the coding that execute different aspects of a transaction between parties.

Decentralized exchanges like Uniswap allow you to swap any token for any other token. This is only possible because pretty much all tokens follow the ERC-20 standard, so Uniswap could write code which works with all tokens following the standard.

Prerequisites for this class.

1 Make sure you have downloaded and installed Metamask.

2 Select the Goerli Testnet network to work with

3 Request some testnet ether on Goerli through any one of the following faucets:
Metamask Faucet
Chainlink Faucet
Paradigm Faucet

Once you have set all of these up, let's get started!

## Now let's get coding

We will use Remix IDE for writing the smart contract. - https://remix.ethereum.org/

In Remix, create a new contract file, I named mine NadosTestToken.sol - you can name it whatever you want!

In the contract, write the following code:

``` 
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol";

contract NadosTestToken is ERC20 {
    constructor(string memory _name, string memory _symbol) ERC20(_name, _symbol) {
        _mint(msg.sender, 10 * 10 ** 18);
    }
}
```

```
pragma solidity ^0.8.0;
```
This line specifies the compiler version of Solidity to be used. ^0.8.0 means any version greater than 0.8.0. 

This line must begin every solidity smart contract.

```
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol";
```

This line imports the ERC-20 token standard from OpenZeppelin (OZ). OZ is an Ethereum security company. Among other things, OZ develops reference contracts for popular smart contract standards which are thoroughly tested and secure. Whenever implementing a smart contract which needs to comply with a standard, try to find an OZ reference implementation rather than rewriting the entire standard from scratch.

OpenZeppelin is an open-source framework to build secure smart contracts. OpenZeppelin provides a complete suite of security products and audit services to build, manage, and inspect all aspects of software development and operations for decentralized applications.

You can look at the implementation of ERC-20 standard contract if you want by following the link - https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol


```
contract NadosTestToken is ERC20 {
    ...
}
```

This specifies a new contract, named LW3Token, in our Solidity file. Also, it says that this contract is an instance of ERC20. ERC20 in this case refers to the standard contract we imported from OpenZeppelin.

```
constructor(string memory _name, string memory _symbol) ERC20(_name, _symbol) {
     ...
}
```

Essentially, a constructor function is what is called when the smart contract is first deployed. Within the constructor, we want two arguments from the user - _name and _symbol which specify the name and symbol of our cryptocurrency. E.g. name = Ethereum, symbol = ETH.

After specifying the constructor function, we will call ERC20(_name, _symbol).

The ERC20 contract we imported from OpenZeppelin has its own constructor, which requires the name and symbol parameters. Since we are extending the ERC20 contract from OpenZeppelin, we need to initialize the ERC20 contract when we deploy ours. So, as part of our constructor, we also need to call the constructor on the ERC20 contract.

```
_mint(msg.sender, 10 * 10 ** 18);
```

_mint is an internal function in solidity within the ERC20 standard contract, which means that it can only be called by the contract itself. External users cannot call this function. That's why it has an underscore before mint.

Since you as the developer want to receive some tokens when you deploy this contract, we call the _mint function to mint some tokens to msg.sender.

_mint takes two arguments - an address to mint to, and the amount of tokens to mint

msg.sender is a global variable injected by the Ethereum Virtual Machine, which is the address which made this transaction. Since you will be the one deploying this contract, your address will be there in msg.sender.

10 * 10 ** 18 specifies that you want 10 full tokens to be minted to your address.


You might want to ask, why "10 * 10 ** 18"?

ERC20 tokens by default work with 18 decimal places. So 1 full NadosTestToken in this case, is actually represented as 10 ^ 18. Therefore, to get 10 full NadosTestToken, we use 10 * 10 ** 18.


#Compiling

So far, we have created NadosTestToken, given it a name and a symbol.

So we will hit the compile button:

![Screenshot 2022-10-01 at 19 42 55](https://user-images.githubusercontent.com/114804772/193424053-3c70aab9-d2cb-45e0-a8b1-19a66d5eeaed.png)

#Deploying

Now go to the Deployer tab in Remix.

Select the Injected Web3 environment (ensure you are on the Ropsten Test Network), and connect your Metamask wallet.

Select the NadosTestToken.sol contract, and enter values for the constructor arguments _name and _symbol.

![Screenshot 2022-10-01 at 19 47 58](https://user-images.githubusercontent.com/114804772/193424213-ab7bbbbe-398e-4296-b762-c30dd2d307c5.png)

When you deploy, you'll get an alert from Metamsk, asking you to pay gas fees.

Gas fees? Yes, we'll discuss that soon.

![Screenshot 2022-10-01 at 19 49 29](https://user-images.githubusercontent.com/114804772/193424265-07f49358-0f84-42cb-ade8-4bbc0de20936.png)

Click Transact and approve the transaction from Metamask to deploy your contract!

When deployed, the contract should show up under the Deployed Contracts section. Click the Copy Address button to copy the contract address.

![Screenshot 2022-10-01 at 19 52 12](https://user-images.githubusercontent.com/114804772/193424349-a7bd6993-95bf-46d5-a8cb-738600da6b76.png)

Now take your new token and go show off in our discord group


#Viewing Tokens in Metamask

You may notice that even though you minted tokens to your address, they don't show up in Metamask.

This is because Metamask cannot detect random ERC20 token balances (since there are literally hundreds of thousands of them). They have a list of the most well known ERC20 tokens that they can show automatically, but apart from that, for your own tokens, you will usually need to tell Metamask to add it to your wallet manually.

To do so:

Copy your contract address

Open Metamask and click Import Tokens in the Assets tab.

![Screenshot 2022-10-01 at 19 59 31](https://user-images.githubusercontent.com/114804772/193424654-c3667dd5-efc4-4d29-9080-a67885bba9e0.png)

![Screenshot 2022-10-01 at 20 00 15](https://user-images.githubusercontent.com/114804772/193424660-c152ef5a-3714-4314-a0d2-09e6c13e8f28.png)

![Screenshot 2022-10-01 at 20 00 30](https://user-images.githubusercontent.com/114804772/193424668-cd335623-6dd4-440a-ad72-bac4d25fc459.png)








