# Build Your First Decentralized Application

This class helps you to create a front end, deploy a Solidity smart contract, and connect them together. We will use Metamask, Remix IDE and Ethers.js.

By the end of this class you will be able to create a simple HTML front end with buttons that can interact with smart contract functions. The tutorial takes place in 3 stages:

Create a basic HTML web page
Create a basic Solidity smart contract
Connect the web page with the smart contracts using Ethers.js

Requirement.

1 Download and Install MetaMask
2 Request some Goerli Tesnet Ether from a faucet loaded into your Metamask Wallet.

Faucet link to request funds - https://faucets.chain.link/
Blog explaining a faucet and how to use one - https://blog.b9lab.com/when-we-first-built-our-faucet-we-deployed-it-on-the-morden-testnet-70bfbf4e317e

3 Install a http server. Use any you like, but we recommend lite-server for beginners:

A. Install Node.js (Download and Instructions)

B. Install lite-server (with NPM in a terminal/command prompt):

### This installs `lite-server` globally (-g) on your computer
```
npm install -g lite-server
```

# Create and Serve a Simple Webpage

The first step is to create a basic HTML page.

-Create a new folder (directory) in your terminal using mkdir <directory name>
-In a code editor (e.g. Atom, or Visual Studio Code), open the folder
-Create a new file called index.html
-Open index.html
-Create HTML boilerplate

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My First dApp</title>
  </head>
  <body></body>
</html>
```

We will create an app that simply reads and writes a value to the blockchain. We will need a label, an input, and buttons.

Inside the body tag, add some text, a label and input.

```
<body>
  <div>
    <h1>This is my dApp!</h1>
    <p>Here we can set or get the mood:</p>
    <label for="mood">Input Mood:</label> <br />
    <input type="text" id="mood" />
  </div>
</body>
```

Inside the div tag add some buttons.

```
<button onclick="getMood()">Get Mood</button>
<button onclick="setMood()">Set Mood</button>
```

```
<style>
  body {
    text-align: center;
    font-family: Arial, Helvetica, sans-serif;
  }

  div {
    width: 20%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
  }

  button {
    width: 100%;
    margin: 10px 0px 5px 0px;
  }
</style>
```

Serve the webpage via terminal/command prompt from the directory that has index.html in it and run:

```
lite-server
```

Go to http://127.0.0.1:3000/ in your browser to see your page!

Your front end is now complete!

  
#Create a Basic Smart Contract

Now it's time to create a Solidity smart contract.

You can use any editor you like to make the contract. For this tutorial we recommend the online IDE Remix.

Go to Remix

Check out the "Solidity Compiler", and "Deploy and Run Transactions" tabs. If they are not present, enable them in the plugin manager

Create a new solidity file in remix, named mood.sol

Write the contract

Specify the solidity version and add a license
  
```
// SPDX-License-Identifier: MIT
 pragma solidity ^0.8.1;
```
  
Define the contract
  
```
contract MoodDiary{

 }
```
  
Inside the contract create a variable called mood

```
  string mood;
```
Next, create Read and Write functions
```
//create a function that writes a mood to the smart contract
 function setMood(string memory _mood) public{
     mood = _mood;
 }

 //create a function the reads the mood from the smart contract
 function getMood() public view returns(string memory){
     return mood;
 }
  ```
  
  
  
  
And that's it, your code should look like:
  
```
//specify the version of solidity
pragma solidity ^0.8.1;

/// a simple set and get function for mood defined: 

//define the contract
contract MoodDiary{
    
    //create a variable called mood
    string mood;
    
    //create a function that writes a mood to the smart contract
    function setMood(string memory _mood) public{
        mood = _mood;
    }
    
    //create a function the reads the mood from the smart contract
    function getMood() public view returns(string memory){
        return mood;
    }
}
 
```
  
  
  
  
  
  


  
  
  
  
  
  
  
  

  
  
  
  
  
  
  
  
  
  
  
 
