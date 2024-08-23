# BeraChain-Auto-Txn-Script By Willzy

You can run it using VPS if you don't have good internet speed :)
- It will work on Github Codespace/ Gitpod / Linux based Terminal (Ubuntu, WSL)
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
- Create a .env file
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
