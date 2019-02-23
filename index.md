## EOSio Software

Cleos is the terminal command to run EOSio actions. EOSio is the software that supports blockchains like EOS, BOS, Telos, Worbli, etc.

This website contains a list of cleos commands so that you can quickly reference them for your convience. 

For instructions on installing EOSio software go to: [github.com/EOSIO/eos](https://github.com/EOSIO/eos)

#### Create Wallet

To start using cleos you will need to create a wallet to manage your private keys.

    cleos wallet create --to-console

Note that you can specify a name for the wallet with the command "-n", otherwise the name will be set to "default".

#### Import Private Key

    cleos wallet import

#### Transfer token

    cleos transfer YOURACCOUNT RECEIVERACCOUNT "1.0000 EOS" "MEMO"

If you wish to transfer a different token you need to specify the contract when calling the action

```
cleos push action cryptopesosc transfer \
        '[ "YOURACCOUNT", "RECEIVERACCOUNT", "100.0000 PSO", "MEMO" ]' -p YOURACCOUNT@active
```

In this example cryptopesosc is the name of the token contract and PSO is the symbol, change these values depending on the token you wish to send.

#### Stake & Unstake

```
cleos system delegatebw YOURACCOUNT RECEIVERACCOUNT "15.0000 EOS" "15.0000 EOS"
cleos system undelegatebw YOURACCOUNT RECEIVERACCOUNT "15.0000 EOS" "15.0000 EOS"
```

#### RAM
```
cleos system buyram YOURACCOUNT RECEIVERACCOUNT "1.0000 EOS"
cleos system sellram YOURACCOUNT 2500
```
Note that the buying amount is specified on EOS and the selling command is determined by the amount of bytes of ram you wish to sell.

#### Create Account

```
cleos system newaccount YOURACCOUNT ACCOUNT2CREATE OWNER_PUB_KEY ACTIVE_PUB_KEY --stake-net "0.1000 EOS" --stake-cpu "0.1000 EOS" --buy-ram-kbytes 5 -p YOURACOCUNT
```

#### Vote Producer

    cleos system voteproducers approve YOURACCOUNT BP_ACCOUNT

### Support or Contact

Feel free to update this command list by creating a Pull Request on [Github](https://github.com/PixelNoob/cleos/)
