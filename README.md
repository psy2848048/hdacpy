# hdacpy

[![Build Status](https://travis-ci.org/psy2848048/hdacpy.svg?branch=master)](https://travis-ci.org/psy2848048/hdacpy)
[![codecov](https://codecov.io/gh/psy2848048/hdacpy/branch/master/graph/badge.svg)](https://codecov.io/gh/psy2848048/hdacpy)

Tools for Hdac wallet management and offline transaction signing  
Forked from hukkinj1/cosmospy

<!--- Don't edit the version line below manually. Let bump2version do it for you. -->
> Version 0.5.5
> Tools for Hdac wallet management and offline transaction signing

## Version matching

| [Hdac](https://github.com/hdac-io/friday) | `hdacpy` |
|------|----------|
| <= 0.9.0 | 0.5.0 |
| <= 0.4.0 | 0.3.3 |
| 0.5.0 | 0.4.0 |

## Installing

Installing from [Hdacpy PyPI repository](https://pypi.org/project/hdacpy):

```bash
pip install hdacpy
```

## Usage

### Prerequisite

Run node & rest-server in following step

* [Installation](https://docs.hdac.io/first-step/installation)
* [Node start](https://docs.hdac.io/first-step/deploy-your-own-friday-testnet)
* [JSON RPC server start](https://docs.hdac.io/restful-api/block-tx)

This library runs on RESTful API

### Generating a wallet

```python
from hdacpy.wallet import generate_wallet
wallet = generate_wallet()
```

The value assigned to `wallet` will be a dictionary just like:

```python
{
    'private_key': '367360433d797cabd35361abdb3f6d0b94d27d7222d3af22a49028b7f4beb85d',
    'public_key': '0320a9b30c5fbbba3ffc34a1732c69365bc2a7de143f970318f8f1a2a38018dc6a',
    'address': 'friday1jg8n39n2m93aavjnxl7snnvt4q6n50g9alxgkl',
    'mnemonic': 'often day image remove film awful art satisfy stable honey provide cactus example flock vacuum adult cool install erase able pencil cancel retreat win'
}
 ```

### Signing transactions

```python
from hdacpy.transaction import Transaction
tx = Transaction(
        host="http://localhost:1317",
        privkey="26d167d549a4b2b66f766b0d3f2bdbe1cd92708818c338ff453abde316a2bd59",
        chain_id="friday-devtest",
    )
tx.transfer(
        token_contract_address="friday1lgharzgds89lpshr7q8kcmd2esnxkfpwmfgk32",
        sender_address="friday1lgharzgds89lpshr7q8kcmd2esnxkfpwmfgk32",
        recipient_address="friday1z47ev5u5ujmc7kwv49tut7raesg55tjyk2wvhd",
        amount=amount, gas_price=2000000, fee=10000
    )
```

`transfer()` executes `POST` to organize tx, and `send_tx()` signs & broadcast the tx.
