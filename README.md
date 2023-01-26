# Uniswap V2 Factory

## Overview

Uniswap Factory allows you to create uniswap liquidity pair contracts and you can fetch the pair address of any ERC20 token that has an active pair.

## Events

`PairCreated`
Emitted each time a pair is created via [createPair](#write).

- Params

| name   | type    | description              |
| :----- | :------ | :----------------------- |
| token0 | address | The address of token0    |
| token1 | address | The address of token1    |
|        | uint    | The final uint log value |

- token0 is guaranteed to be strictly less than token1 by sort order.

- The final uint log value will be 1 for the first pair created, 2 for the second, etc.

## Functions

### WRITE

`createPair`

Creates a pair for tokenA and tokenB if one doesn't exist already.

- Event

  Emits [PairCreated](#events)

- Params

  | name   | type    | description            |
  | :----- | :------ | :--------------------- |
  | tokenA | address | The address of token A |
  | tokenB | address | The address of token B |

`setFeeTo`

Set fee address by setter.

- Params

  | name    | type    | description        |
  | :------ | :------ | :----------------- |
  | \_feeTo | address | The address of fee |

`setFeeToSetter`

Set a new setter address by **older setter**.

- Params

  | name          | type    | description                 |
  | :------------ | :------ | :-------------------------- |
  | \_feeToSetter | address | The address of a new setter |

## Read

`feeTo`

Get address to which commission fee is sent.

`feeToSetter`

The address allowed to change [feeTo](#read)

`getPair`

Returns the address of the pair for tokenA and tokenB, if it has been created, else address(0)

`allPairs`

Returns the address of the nth pair (0-indexed) created through the factory, or address(0) (0x0000000000000000000000000000000000000000) if not enough pairs have been created yet.

- Pass 0 for the address of the first pair created, 1 for the second, etc.

## Local Development

The following assumes the use of `node@>=10`.

### Install Dependencies

`yarn`

### Compile Contracts

`yarn compile`

### Run Tests

`yarn test`
