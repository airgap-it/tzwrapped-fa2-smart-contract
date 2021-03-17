# tzETH Implementation

This implementation is a FA2 compatible token contract which covers the same requirements like the 
already existing tzBTC (which is FA1.2). 

This implementation derived the required functionality from the [tzBTC project](https://github.com/tz-wrapped/tezos-btc). 

The multisig functionality has been put in a different repository which can be found here:

There are two main differences compared to the mentioned tzBTC project:

- FA2 allows for multiple tokens on the same contract. This of course means that we can have per token
an admin who gets the token 'admin' status as per FA1.2.


This is the mapping of entrypoint names used tzBTC to tzETH:

| entrypoint tzBTC | entrypoint tzETH |
|------------------|------------------|
| getVersion       | no upgrade support          |
| getBalance       | balance_of                  |
| getTotalSupply   | total_supply (offchain)     |
| getTotalMinted   | total_minted (offchain)     |
| getTotalBurned   | total_burned (offchain)     |
| getOwner         | is_administrator (offchain) |
| getRedeemAddress | get_redeem_addresses    |
| getTokenMetaData | %token_metadata bigmap  |
| Run              | no upgrade support      |
| Upgrade          | no upgrade support      |
| epwBeginUpgrade  | no upgrade support      |
| epwApplyMigration| no upgrade support      |
| epwSetCode       | no upgrade support      |
| epwFinishUpgrade | no upgrade support      |
| Transfer         | transfer                |
| Approve          | update_operators        |
| Mint             | mint                    |
| Burn             | burn                    |
| addOperator      | see multisig            |
| removeOperator   | see multisig            | 
| setRedeemAddress | set_redeem_address      |
| Pause            | pause                   |
| Unpause          | unpause                 |
| transferOwnership| propose_administrator/remove_administrator   |
| acceptOwnership  | set_administrator       |

## Build/Basic Usage

### Dependencies

This project depends only on SmartPy, you can install SmartPy by doing a:

```
$ sh <(curl -s https://smartpy.io/cli/install.sh)
```

You can read more about the installation here: https://smartpy.io/cli/

If you feel lazy you can simply copy/paste the entire 'tzwrapped-fa2.py' content into the web IDE: https://smartpy.io/ide 

### Build

```
$ /home/coder/smartpy-cli/SmartPy.sh compile tzwrapped-fa2.py "TzWrappedFA2({administrator.address:True})" out
```

### Test
```
$ /home/coder/smartpy-cli/SmartPy.sh test tzwrapped-fa2.py out
```