# Setting up Smart Contract development environment 

## Things you need for setup
1. *TestRPC*: TestRPC is an ethereum client for testing and development. This simulates a blockchain without mining and gives you a setup with randomly generated accounts.
   *Installation*
   ```
   npm install -g ethereumjs-testrpc
   ```
   *Run testRPC*
   ```
   testrpc
   ```

2. *Truffle*: Truffle is a framewrok that we will be using to develop smart contracts.
   *Installation*
   ```
   npm install -g truffle
   ```
   *create a new project*
   ```
   mkdir test
   cd test
   truffle init
   
   Downloading project...
   Project initialized.

  Documentation: http://truffleframework.com/docs

  Commands:

  Compile: truffle compile
  Migrate: truffle migrate
  Test:    truffle test
  ```
  *Tree structure of truffle project*
  ```
  ├── contracts
  │   ├── ConvertLib.sol
  │   ├── MetaCoin.sol
  │   └── Migrations.sol
  ├── migrations
  │   ├── 1_initial_migration.js
  │   └── 2_deploy_contracts.js
  ├── test
  │   ├── TestMetacoin.sol
  │   └── metacoin.js
  └── truffle.js
  ```
