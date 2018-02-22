# HushCoin

## Main Introduction

HushCoin is a research project exploring the fundation of blockchain that we hope have a better understanding about blockchain through this project.

## Environment

1. First of all, python 3.6.4+, pip, Flask, requests is needed.
2. A http client is neccesary, we recommend to use Postman, cURL and so on.

## Structure

### Blockchain Class

In this part of code, we intend to build a Blockchain class, creating two lists in the constructor, one for storing blockchain(def new_block) and one for storing transactions(def new_transaction).

### Block

A good block should include such characters: index, timestamp, transactions, proof, previous hash.

Here comes an example:
```
block = {
    'index': 1,
    'timestamp': 6057125.900785,
    'transactions': [
        {
            'sender': "527147fe1f6f9dd545de4b27ee00",
            'recipient': "f5cdfa2934df3954a5c7c7da5df1f",
            'amount': 5,
        }
    ],
    'proof': 34774000,
    'previous_hash': "f24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
}
```

### API

We intend to build 3 API:
1. /transactions/new (create a new transaction and add it to block) 
2. /mine (deliver to the server to dig new block)
3. /chain (return the whole blockchain)
