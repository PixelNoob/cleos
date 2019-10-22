#### Create the contract account

    cleos system newaccount YOUR_ACCOUNT CONTRACT_ACCOUNT OWNER_KEY ACTIVE_ACCOUNT --stake-net "0.1000 EOS" --stake-cpu "0.1000 EOS" --buy-ram-kbytes 200 -p YOUR_ACCOUNT@active

#### Download the contract repository

Download the contracts from: [github.com/eosio/eosio.contracts](https://github.com/eosio/eosio.contracts)

#### Generate the wasm

Go to the eosio.token folder and generate the wasm ([you need to have eosio.cdt installed](https://developers.eos.io/eosio-home/docs/installing-the-contract-development-toolkit))

    eosio-cpp -I include -o eosio.token.wasm src/eosio.token.cpp --abigen

#### Set contract on Account

    cleos set contract CONTRACT_ACCOUNT folder_to/eosio.token -p CONTRACT_ACCOUNT@active

#### Create Token

    cleos push action CONTRACT_ACCOUNT create '[ "CONTRACT_ACCOUNT", "1000000000.0000 SYMBOL"]' \
         -p CONTRACT_ACCOUNT@active

#### Issue Token

    cleos push action CONTRACT_ACCOUNT issue '[ "CONTRACT_ACCOUNT", "0.0001 SYMBOL", "issue" ]' \
        -p CONTRACT_ACCOUNT@active

#### Verify token balance

    cleos get currency balance CONTRACT_ACCOUNT CONTRACT_ACCOUNT SYMBOL

#### Transfer token

    cleos push action CONTRACT_ACCOUNT transfer \
        '[ "CONTRACT_ACCOUNT", "OTHER_ACCOUNT", "100000.0000 SYMBOL", "MEMO" ]' -p CONTRACT_ACCOUNT@active

#### Retire Token

    cleos push action CONTRACT_ACCOUNT retire '["0.0001 SYMBOL", "retire"]' -p CONTRACT_ACCOUNT@active


## More Guides

* [Cleos commands](/cleos)
