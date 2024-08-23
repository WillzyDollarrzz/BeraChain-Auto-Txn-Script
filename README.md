# BeraChain-Auto-Txn-Script By Willzy

You can run it using VPS if you don't have good internet speed :)
- You can use Github Codespace/ Gitpod / Linux based Terminal (Ubuntu, WSL)
- In this guide we're using Linux based Terminal (Ubuntu, WSL)
- You can as well use node.js with npm package manager

-  Navigate to home directory
  
```bash
cd $HOME
```
- Create a Folder in directory and open it
```bash
mkdir berachain-auto-tx && cd berachain-auto-tx
```
- Create a `.env` file
  ```bash
  nano .env
  ```
- Paste this with your edited details
  
    ```bash
  PRIVATE_KEY=your-private-key
  BARTIO_RPC_URL=https://bartio.rpc.berachain.com
  TARGET_ADDRESS=your-target-address
  ```
  In the above code,
  - replace ```your-private-key``` with the private key of your wallet containing $bera tokens (without the 0x)
  - replace ```your-target-address``` with the wallet address you want your $bera tokens to be sent to.
  - Ctrl `X` + `Y` + `enter` to save


- Create And Edit The Script File
  ```bash
  nano bera-tx.js
  ```
- Do not edit this, Paste as is.

```bash
require('dotenv').config();
const { ethers } = require('ethers');

// Set up provider and wallet
const provider = new ethers.JsonRpcProvider(process.env.BARTIO_RPC_URL);
const wallet = new ethers.Wallet(process.env.PRIVATE_KEY, provider);

// Amount to transfer (0.00001 BERA in Wei)
const amountToSend = ethers.parseUnits('0.00001', 'ether');

// Set the target address
const targetAddress = process.env.TARGET_ADDRESS;

// Function to send a transaction
const sendTransaction = async () => {
    try {
        const tx = await wallet.sendTransaction({
            to: targetAddress,
            value: amountToSend,
        });
        await tx.wait(); // Wait for the transaction to be mined
        console.log(`Transferred 0.00001 BERA to ${targetAddress}. Transaction Hash: ${tx.hash}`);
    } catch (error) {
        console.error(`Error sending transaction to ${targetAddress}:`, error);
    }
};

// Main function to execute the transfers every 5 seconds
const startAutoTransfers = () => {
    setInterval(async () => {
        await sendTransaction();
    }, 5000); // 5-second interval
};

startAutoTransfers();

```
- Ctrl `X` + `Y` + `enter` to exit

Before we execute the script, let's make sure some packages and dependencies are installed and up-to-date

```bash
sudo apt update
```
```bash
sudo apt upgrade -y
```
- Node.js and npm installation
  
  ```bash
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash && export NVM_DIR="/usr/local/share/nvm"; [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"; [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"; source ~/.bashrc; nvm install --lts; nvm use --lts
  ```
- Check version 
```bash
node -v && npm -v
```
- Installing Dependencies 
```bash
npm init -y
``` 
```bash
npm install ethers dotenv
```
- Installing ethers.js v6
```bash
npm install ethers@6
```

- Now let's run the Script

```bash
node bera-tx.js
```

Yayy🤗... it worked.

- If you encountered any error, let me know on [twitter](https://x.com/willzydollarrzz)

- To support, Donate:
  `0xb09D24107aC152EfACcf101986745e3d3c2Bb258`
