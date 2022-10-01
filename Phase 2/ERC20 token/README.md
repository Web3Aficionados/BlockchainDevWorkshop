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

contract LW3Token is ERC20 {
    constructor(string memory _name, string memory _symbol) ERC20(_name, _symbol) {
        _mint(msg.sender, 10 * 10 ** 18);
    }
}
```










