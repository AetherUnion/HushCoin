# HushCoin

## Main Introduction

HushCoin is a research project exploring the fundation of blockchain that we hope have a better understanding about blockchain through this project.

## Environment

1. First of all, python 3.6.4+, pip, Flask, requests is needed.
2. A http client is neccesary, we recommend to use Postman, cURL and so on.

## Structure

### Blockchain Class

In this part of code, we intend to build a Blockchain class, creating two lists in the constructor, one for storing blockchain(def new_block) and one for storing transactions(```def new_transaction```).

### Block

A good block should include such characters: ```index```, ```timestamp```, ```transactions```, ```proof```, ```previous hash```.

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
1. ```/transactions/new``` (create a new transaction and add it to block) 
2. ```/mine``` (deliver to the server to dig new block)
3. ```/chain``` (return the whole blockchain)

### Run

Now, we are gonna to run the blockchain through http client. We reccomend Postman and cURL.
Start the server:
```
$ name.py
* Runing on a http (CTRL + C to quit)
```
Open http://localhost:5000/mine to dig mine and add a new transaction through post request. Then request http://localhost:5000/chain to check all the block information.

## Consistency

Till now we have finished a basic blockchain that could dig mine and recieve transaction. In order to make sure the blockchain system is distributed, we need to develop a consistent algorithm.

### Register Node

In this part we intend to find a method to let a node grasp their neibor nodes which means each node need to save a record that contains other nodes in the whole network.

So, some new API should be added:
1. ```/nodes/register``` (recieve a new node list in URL form)
2. ```/nodes/resolve```(run the consistent algorithm, solve conflict and make sure that node has a correct chain)

### Consistent Algorithm

Conflict means different nodes have different chains and aiming to solve this problem, we think the longest chain is effective and it is the terminal chain.

This algorithm is very important and we use two methods to achieve it.
1. ```valid_chain()``` This method is used to tranverse all the hash and proof to check whether the chain is effective.
2. ```resolve_conflicts()``` This menthod is used to solve conflict.

You could run the node in different service or open different network port in one service. When you run it, two nodes will be activate: http://localhost:5000 and http://localhost:5001
```
pipenv run python name.py
pipenv run python name.py -p 5001
```

Then we could invit your friends to test our blockchain
