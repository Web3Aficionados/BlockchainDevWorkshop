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
