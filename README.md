# Optino Governance DAO Smart Contracts

Status: **Work In Progress**

The Optino Governance (OptinoGov) smart contract is the Decentralised Autonomous Organisation (DAO) that operates the Optino Vending Machine.

Optino Governance token (OGToken) holders lock their OGTokens into the OptinoGov smart contract to submit and vote on proposals. If successful, the proposal will be executed, e.g., the minting of new OGTokens, the burning of staked tokens, and setting of fee rates.

When OGTOkens are locked into the OptinoGov smart contract, the equivalent number of Optino Governance Dividend token (OGDToken) are minted. These tokens will accrue fees generated by the Optino Vending Machine.

Following are the main smart contracts:

* [contracts/OptinoGov.sol](contracts/OptinoGov.sol) - [flattened](flattened/OptinoGov_flattened.sol)
* [contracts/OGToken.sol](contracts/OGToken.sol) - [flattened](flattened/OGToken_flattened.sol)
* [contracts/OGDToken.sol](contracts/OGDToken.sol) - [flattened](flattened/OGDToken_flattened.sol)

See also:

* https://wiki.optino.io

<br />

<hr />

### Remix

To test out these smart contracts in [Remix](http://remix.ethereum.org/), copy the contents of the files above into the same file names within Remix. Comment out the local `import ".\{file.sol}"` and uncomment the GitHub `import "https://github.com/ogDAO/Governance/blob/master/contracts/{file}.sol";`.

<br />

<hr />

### Testing

#### Clone Repository
Check out this repository into your projects subfolder:

```
git clone https://github.com/ogDAO/Governance.git
cd Governance
```

<br />

#### Install And Run Go Ethereum

Install [Go-Ethereum](https://github.com/ethereum/go-ethereum) (also known as `geth`) on your local computer to run a development blockchain node for testing. Or install and use [Ganache](https://www.trufflesuite.com/ganache) instead.

If you have installed `geth`, run:

```
./00_runGeth.sh
./01_unlockAndFundAccounts.sh
```

You may need to `chmod 700 00_runGeth.sh 01_unlockAndFundAccounts.sh` before being able to execute it.

<br />

#### Install Truffle


If not already installed, you will need [NPM](https://www.npmjs.com/). [NVM](https://github.com/nvm-sh/nvm) may take away some of your NPM versioning pain.

You will need to install [Truffle](https://github.com/trufflesuite/truffle):

```
npm install -g truffle
```

<br />

#### Install Truffle Flattener And Flatten Solidity Files

You may want to to install [Truffle Flattener](https://github.com/nomiclabs/truffle-flattener) using the command:

```
npm install -g truffle-flattener
./10_flattenSolidityFiles.sh
```

The flattened files can be found in the [./flattened/](./flattened/) subdirectory.

<br />

#### Install Other Modules

You will need the following modules installed:

```
npm install --save web3@1.2.1
npm install --save ethers
npm install --save eth-sig-util
npm install --save bignumber.js

```

<br />

#### Compile

```
truffle compile
```

<br />

#### Run OptinoGov Tests

```
truffle test test/TestOptinoGov.test.js
```

Sample output:

```
Iota:Governance bok$ truffle test test/TestOptinoGov.test.js
Using network 'development'.


Compiling your contracts...
===========================
> Everything is up to date, there is nothing to compile.

TestToken.test.js: describe(TestToken behavior tests)


  Contract: Test OptinoGov
--- Setup completed ---
RESULT:  # Account                                             EtherBalanceChange                             OG                            OGD @ 183 -> 191
RESULT:                                                                                                      FEE
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT: 0 0xa00Af22D07c87d96EeeB0Ed583f8F6AC7812827E         0.000000000000000000       10000.000000000000000000           0.000000000000000000 Owner:0xa00A
RESULT:                                                                                     0.000000000000000000
RESULT: 1 0xa11AAE29840fBb5c86E6fd4cF809EBA183AEf433         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User1:0xa11A
RESULT:                                                                                     0.000000000000000000
RESULT: 2 0xa22AB8A9D641CE77e06D98b7D7065d324D3d6976         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User2:0xa22A
RESULT:                                                                                     0.000000000000000000
RESULT: 3 0xa33a6c312D9aD0E0F2E95541BeED0Cc081621fd0         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User3:0xa33a
RESULT:                                                                                     0.000000000000000000
RESULT: 4 0x3d98693e0d665a075eDf9Aacd28169EB787fe993         0.000000000000000000           0.000000000000000000           0.000000000000000000 OGToken:0x3d98
RESULT:                                                                                     0.000000000000000000
RESULT: 5 0x71130A1a433B047069Cb1e7b16923d081458d40f         0.000000000000000000           0.000000000000000000           0.000000000000000000 OGDToken:0x7113
RESULT:                                                                                     0.000000000000000000
RESULT: 6 0x32463D05d5F5443AdC9720137A5d4a50341C6c7e         0.000000000000000000           0.000000000000000000           0.000000000000000000 FeeToken:0x3246
RESULT:                                                                                     0.000000000000000000
RESULT: 7 0x83Dd10d39d0aB60A52E08050959f9BcC61b0D4dF         0.000000000000000000           0.000000000000000000           0.000000000000000000 OptinoGov:0x83Dd
RESULT:                                                                                     0.000000000000000000
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:                                                                                 40000.000000000000000000           0.000000000000000000 Total Token Balances
RESULT:                                                                                     0.000000000000000000
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:
RESULT: Token 0 OGToken:0x3d98 @ 0x3d98693e0d665a075eDf9Aacd28169EB787fe993
RESULT: - symbol               : OG
RESULT: - name                 : Optino Governance
RESULT: - decimals             : 18
RESULT: - totalSupply          : 40000
RESULT: - owner                : OptinoGov:0x83Dd
RESULT: Token 1 OGDToken:0x7113 @ 0x71130A1a433B047069Cb1e7b16923d081458d40f
RESULT: - symbol               : OGD
RESULT: - name                 : Optino Governance Dividend
RESULT: - decimals             : 18
RESULT: - totalSupply          : 0
RESULT: - owner                : OptinoGov:0x83Dd
RESULT: - dividendTokenLength  : 2
RESULT: - dividendTokens       : 0 FeeToken:0x3246
RESULT: - dividendTokens       : 1 0x0000000000000000000000000000000000000000
RESULT: Token 2 FeeToken:0x3246 @ 0x32463D05d5F5443AdC9720137A5d4a50341C6c7e
RESULT: - symbol               : FEE
RESULT: - name                 : Fee
RESULT: - decimals             : 18
RESULT: - totalSupply          : 0
RESULT: - owner                : Owner:0xa00A
RESULT: OptinoGov OptinoGov:0x83Dd @ 0x83Dd10d39d0aB60A52E08050959f9BcC61b0D4dF
RESULT: - ogToken              : OGToken:0x3d98
RESULT: - ogdToken             : OGDToken:0x7113
RESULT: - maxLockTerm          : 1000 seconds = 0.01157407407407407407 days
RESULT: - rewardsPerSecond     : 150000000000000000 = 12960 per day
RESULT: - proposalCost         : 100000000000000000000 = 100
RESULT: - proposalThreshold    : 1000000000000000 = 0.1%
RESULT: - quorum               : 200000000000000000 = 20%
RESULT: - quorumDecayPerSecond : 12683916793 = 39.9999999984048% per year
RESULT: - votingDuration       : 10 seconds = 0.00011574074074074074 days
RESULT: - executeDelay         : 10 seconds = 0.00011574074074074074 days
RESULT: - rewardPool           : 0 = 0
RESULT: - totalVotes           : 0 = 0
RESULT: - proposalCount        : 0
RESULT: - stakeInfoLength      : 0
RESULT:  # Account                                             EtherBalanceChange                             OG                            OGD @ 183 -> 195
RESULT:                                                                                                      FEE
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT: 0 0xa00Af22D07c87d96EeeB0Ed583f8F6AC7812827E         0.014778000000000000       10000.000000000000000000           0.000000000000000000 Owner:0xa00A
RESULT:                                                                                     0.000000000000000000
RESULT: 1 0xa11AAE29840fBb5c86E6fd4cF809EBA183AEf433        -0.005726000000000000        9000.000000000000000000        1000.000000000000000000 User1:0xa11A
RESULT:                                                                                     0.000000000000000000
RESULT: 2 0xa22AB8A9D641CE77e06D98b7D7065d324D3d6976        -0.004526000000000000        9000.000000000000000000        1000.000000000000000000 User2:0xa22A
RESULT:                                                                                     0.000000000000000000
RESULT: 3 0xa33a6c312D9aD0E0F2E95541BeED0Cc081621fd0        -0.004526000000000000        9000.000000000000000000        1000.000000000000000000 User3:0xa33a
RESULT:                                                                                     0.000000000000000000
RESULT: 4 0x3d98693e0d665a075eDf9Aacd28169EB787fe993         0.000000000000000000           0.000000000000000000           0.000000000000000000 OGToken:0x3d98
RESULT:                                                                                     0.000000000000000000
RESULT: 5 0x71130A1a433B047069Cb1e7b16923d081458d40f         0.000000000000000000           0.000000000000000000           0.000000000000000000 OGDToken:0x7113
RESULT:                                                                                     0.000000000000000000
RESULT: 6 0x32463D05d5F5443AdC9720137A5d4a50341C6c7e         0.000000000000000000           0.000000000000000000           0.000000000000000000 FeeToken:0x3246
RESULT:                                                                                     0.000000000000000000
RESULT: 7 0x83Dd10d39d0aB60A52E08050959f9BcC61b0D4dF         0.000000000000000000        3000.000000000000000000           0.000000000000000000 OptinoGov:0x83Dd
RESULT:                                                                                     0.000000000000000000
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:                                                                                 40000.000000000000000000        3000.000000000000000000 Total Token Balances
RESULT:                                                                                     0.000000000000000000
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:
RESULT: Token 0 OGToken:0x3d98 @ 0x3d98693e0d665a075eDf9Aacd28169EB787fe993
RESULT: - symbol               : OG
RESULT: - name                 : Optino Governance
RESULT: - decimals             : 18
RESULT: - totalSupply          : 40000
RESULT: - owner                : OptinoGov:0x83Dd
RESULT: Token 1 OGDToken:0x7113 @ 0x71130A1a433B047069Cb1e7b16923d081458d40f
RESULT: - symbol               : OGD
RESULT: - name                 : Optino Governance Dividend
RESULT: - decimals             : 18
RESULT: - totalSupply          : 3000
RESULT: - owner                : OptinoGov:0x83Dd
RESULT: - dividendTokenLength  : 2
RESULT: - dividendTokens       : 0 FeeToken:0x3246
RESULT: - dividendTokens       : 1 0x0000000000000000000000000000000000000000
RESULT: Token 2 FeeToken:0x3246 @ 0x32463D05d5F5443AdC9720137A5d4a50341C6c7e
RESULT: - symbol               : FEE
RESULT: - name                 : Fee
RESULT: - decimals             : 18
RESULT: - totalSupply          : 0
RESULT: - owner                : Owner:0xa00A
RESULT: OptinoGov OptinoGov:0x83Dd @ 0x83Dd10d39d0aB60A52E08050959f9BcC61b0D4dF
RESULT: - ogToken              : OGToken:0x3d98
RESULT: - ogdToken             : OGDToken:0x7113
RESULT: - maxLockTerm          : 1000 seconds = 0.01157407407407407407 days
RESULT: - rewardsPerSecond     : 150000000000000000 = 12960 per day
RESULT: - proposalCost         : 100000000000000000000 = 100
RESULT: - proposalThreshold    : 1000000000000000 = 0.1%
RESULT: - quorum               : 200000000000000000 = 20%
RESULT: - quorumDecayPerSecond : 12683916793 = 39.9999999984048% per year
RESULT: - votingDuration       : 10 seconds = 0.00011574074074074074 days
RESULT: - executeDelay         : 10 seconds = 0.00011574074074074074 days
RESULT: - rewardPool           : 0 = 0
RESULT: - totalVotes           : 1500000000000000000000 = 1500
RESULT: - proposalCount        : 0
RESULT: - stakeInfoLength      : 0
    ✓ Test OptinoGov Lock Tokens (4532ms)


  1 passing (13s)
```

<br />

#### Run OGDToken Tests

```
truffle test test/TestOGDToken.test.js
```

Sample output:

```
Iota:Governance bok$ truffle test test/TestOGDToken.test.js
Using network 'development'.


Compiling your contracts...
===========================
> Everything is up to date, there is nothing to compile.

TestOGDToken.test.js: describe(OGToken behavior tests)


  Contract: Test OGDToken
--- Setup completed ---
RESULT:  # Account                                             EtherBalanceChange                            OGD                            FEE @ 4856 -> 4860
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT: 0 0xa00Af22D07c87d96EeeB0Ed583f8F6AC7812827E         0.000000000000000000           0.000000000000000000       10000.000000000000000000 Owner:0xa00A
RESULT: 1 0xa11AAE29840fBb5c86E6fd4cF809EBA183AEf433         0.000000000000000000           0.000000000000000000           0.000000000000000000 User1:0xa11A
RESULT: 2 0xa22AB8A9D641CE77e06D98b7D7065d324D3d6976         0.000000000000000000           0.000000000000000000           0.000000000000000000 User2:0xa22A
RESULT: 3 0xa33a6c312D9aD0E0F2E95541BeED0Cc081621fd0         0.000000000000000000           0.000000000000000000           0.000000000000000000 User3:0xa33a
RESULT: 4 0x90baFC503D68264569B73451804e5a8aeaD119C9         0.000000000000000000           0.000000000000000000           0.000000000000000000 OGDToken:0x90ba
RESULT: 5 0xB0F4f96c4F39089BFdD8BaBf0E6148fa8cf0e75E         0.000000000000000000           0.000000000000000000           0.000000000000000000 FeeToken:0xB0F4
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:                                                                                     0.000000000000000000       10000.000000000000000000 Total Token Balances
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:
RESULT: Token 0 OGDToken:0x90ba @ 0x90baFC503D68264569B73451804e5a8aeaD119C9
RESULT: - symbol               : OGD
RESULT: - name                 : Optino Governance Dividend
RESULT: - decimals             : 18
RESULT: - totalSupply          : 0
RESULT: - owner                : Owner:0xa00A
RESULT: - dividendTokensLength : 2
RESULT: - dividendToken        : 0 FeeToken:0xB0F4, enabled: true, unclaimedDividends: 0 = 0
RESULT: - dividendToken        : 1 ETH:0x0000, enabled: true, unclaimedDividends: 0 = 0
RESULT: - dividendsOwing       : 1 User1:0xa11A
RESULT:   -                    : FeeToken:0xB0F4 0 0
RESULT:   -                    : ETH:0x0000 0 0
RESULT: - dividendsOwing       : 2 User2:0xa22A
RESULT:   -                    : FeeToken:0xB0F4 0 0
RESULT:   -                    : ETH:0x0000 0 0
RESULT: - dividendsOwing       : 3 User3:0xa33a
RESULT:   -                    : FeeToken:0xB0F4 0 0
RESULT:   -                    : ETH:0x0000 0 0
RESULT: Token 1 FeeToken:0xB0F4 @ 0xB0F4f96c4F39089BFdD8BaBf0E6148fa8cf0e75E
RESULT: - symbol               : FEE
RESULT: - name                 : Fee
RESULT: - decimals             : 18
RESULT: - totalSupply          : 10000
RESULT: - owner                : Owner:0xa00A
RESULT:
RESULT: --- Minting 10,000 OGD tokens for users{1..3}, Owner approve 100 FEE for OGToken to spend ---
RESULT: --- Owner depositing as dividends 100 FEE and 10 ETH ---
RESULT:  # Account                                             EtherBalanceChange                            OGD                            FEE @ 4856 -> 4864
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT: 0 0xa00Af22D07c87d96EeeB0Ed583f8F6AC7812827E       -10.000000000000000000           0.000000000000000000        9900.000000000000000000 Owner:0xa00A
RESULT: 1 0xa11AAE29840fBb5c86E6fd4cF809EBA183AEf433         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User1:0xa11A
RESULT: 2 0xa22AB8A9D641CE77e06D98b7D7065d324D3d6976         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User2:0xa22A
RESULT: 3 0xa33a6c312D9aD0E0F2E95541BeED0Cc081621fd0         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User3:0xa33a
RESULT: 4 0x90baFC503D68264569B73451804e5a8aeaD119C9        10.000000000000000000           0.000000000000000000         100.000000000000000000 OGDToken:0x90ba
RESULT: 5 0xB0F4f96c4F39089BFdD8BaBf0E6148fa8cf0e75E         0.000000000000000000           0.000000000000000000           0.000000000000000000 FeeToken:0xB0F4
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:                                                                                 30000.000000000000000000       10000.000000000000000000 Total Token Balances
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:
RESULT: Token 0 OGDToken:0x90ba @ 0x90baFC503D68264569B73451804e5a8aeaD119C9
RESULT: - symbol               : OGD
RESULT: - name                 : Optino Governance Dividend
RESULT: - decimals             : 18
RESULT: - totalSupply          : 30000
RESULT: - owner                : Owner:0xa00A
RESULT: - dividendTokensLength : 2
RESULT: - dividendToken        : 0 FeeToken:0xB0F4, enabled: true, unclaimedDividends: 100000000000000000000 = 100
RESULT: - dividendToken        : 1 ETH:0x0000, enabled: true, unclaimedDividends: 10000000000000000000 = 10
RESULT: - dividendsOwing       : 1 User1:0xa11A
RESULT:   -                    : FeeToken:0xB0F4 33333333333333333000 33.333333333333333
RESULT:   -                    : ETH:0x0000 3333333333333333000 3.333333333333333
RESULT: - dividendsOwing       : 2 User2:0xa22A
RESULT:   -                    : FeeToken:0xB0F4 33333333333333333000 33.333333333333333
RESULT:   -                    : ETH:0x0000 3333333333333333000 3.333333333333333
RESULT: - dividendsOwing       : 3 User3:0xa33a
RESULT:   -                    : FeeToken:0xB0F4 33333333333333333000 33.333333333333333
RESULT:   -                    : ETH:0x0000 3333333333333333000 3.333333333333333
RESULT: Token 1 FeeToken:0xB0F4 @ 0xB0F4f96c4F39089BFdD8BaBf0E6148fa8cf0e75E
RESULT: - symbol               : FEE
RESULT: - name                 : Fee
RESULT: - decimals             : 18
RESULT: - totalSupply          : 10000
RESULT: - owner                : Owner:0xa00A
RESULT:
RESULT: --- Users{1..3} withdrawing ---
RESULT:  # Account                                             EtherBalanceChange                            OGD                            FEE @ 4856 -> 4866
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT: 0 0xa00Af22D07c87d96EeeB0Ed583f8F6AC7812827E        -9.994128300000000000           0.000000000000000000        9900.000000000000000000 Owner:0xa00A
RESULT: 1 0xa11AAE29840fBb5c86E6fd4cF809EBA183AEf433        -0.002702940000000000       10000.000000000000000000           0.000000000000000000 User1:0xa11A
RESULT: 2 0xa22AB8A9D641CE77e06D98b7D7065d324D3d6976        -0.003168760000000000       10000.000000000000000000           0.000000000000000000 User2:0xa22A
RESULT: 3 0xa33a6c312D9aD0E0F2E95541BeED0Cc081621fd0         0.000000000000000000       10000.000000000000000000           0.000000000000000000 User3:0xa33a
RESULT: 4 0x90baFC503D68264569B73451804e5a8aeaD119C9        10.000000000000000000           0.000000000000000000         100.000000000000000000 OGDToken:0x90ba
RESULT: 5 0xB0F4f96c4F39089BFdD8BaBf0E6148fa8cf0e75E         0.000000000000000000           0.000000000000000000           0.000000000000000000 FeeToken:0xB0F4
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:                                                                                 30000.000000000000000000       10000.000000000000000000 Total Token Balances
RESULT: -- ------------------------------------------ --------------------------- ------------------------------ ------------------------------ ---------------------------
RESULT:
RESULT: Token 0 OGDToken:0x90ba @ 0x90baFC503D68264569B73451804e5a8aeaD119C9
RESULT: - symbol               : OGD
RESULT: - name                 : Optino Governance Dividend
RESULT: - decimals             : 18
RESULT: - totalSupply          : 30000
RESULT: - owner                : Owner:0xa00A
RESULT: - dividendTokensLength : 2
RESULT: - dividendToken        : 0 FeeToken:0xB0F4, enabled: true, unclaimedDividends: 33333333333333334000 = 33.333333333333334
RESULT: - dividendToken        : 1 ETH:0x0000, enabled: true, unclaimedDividends: 3333333333333334000 = 3.333333333333334
RESULT: - dividendsOwing       : 1 User1:0xa11A
RESULT:   -                    : FeeToken:0xB0F4 0 0
RESULT:   -                    : ETH:0x0000 0 0
RESULT: - dividendsOwing       : 2 User2:0xa22A
RESULT:   -                    : FeeToken:0xB0F4 0 0
RESULT:   -                    : ETH:0x0000 0 0
RESULT: - dividendsOwing       : 3 User3:0xa33a
RESULT:   -                    : FeeToken:0xB0F4 33333333333333333000 33.333333333333333
RESULT:   -                    : ETH:0x0000 3333333333333333000 3.333333333333333
RESULT: Token 1 FeeToken:0xB0F4 @ 0xB0F4f96c4F39089BFdD8BaBf0E6148fa8cf0e75E
RESULT: - symbol               : FEE
RESULT: - name                 : Fee
RESULT: - decimals             : 18
RESULT: - totalSupply          : 10000
RESULT: - owner                : Owner:0xa00A
RESULT:
    ✓ Test OGDToken worksflow (6497ms)


  1 passing (11s)
```

<br />

#### Debug

```
truffle debug {txHash}
```

<br />

#### Migrate

```
truffle migrate [--reset]
```

<br />

<br />

Enjoy!

(c) The Optino Project 2020. GPLv2
