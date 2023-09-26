# Start

## 1. Via npm in browser

### Install

```bash
npm i paywithcoin-sdk
```

### Create transaction

```ts
import {createTransactionSimple} from 'paywithcoin-sdk';

const transaction = await createTransactionSimple({
  name: 'Orange' // transaction name
  fiat: {
    id: 'USD',
    amount: 1, // transaction price
  },
  cryptoOptions: {
    id: 'XLM', // crypto currency
    address: 'GDO6KD...', // your address
  },
});
```

### Open payment widget in new tab

```ts
import {openTab} from 'paywithcoin-sdk';

openTab(transaction.code);
```

### Start track transaction in current web page

```ts
import {startCheck} from 'paywithcoin-sdk';

startCheck({
  transactionCode: transaction.code,
  onSuccess: (transaction) => {
    alert('Transaction success');
  },
  onFail: (transaction) => {
    alert('Transaction failed');
  },
});
```

## 2. Via http fetch

### Create transacion

```ts
const response = await fetch('https://paywithcoin.vercel.app/api/transactions', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    name: 'Test name',
    fiat: {
      id: 'USD',
      amount: 1,
    },
    crypto_options: [
      {
        id: 'XLM:test',
        name: 'stellar testnet',
        code: 'XLM',
        address: 'GDO6KDYV5RRNJRFZEPYUTFTBMTGQOWCBDB2OZ74EWV32BHXKX6KTNHHA',
      },
    ],
  }),
});

const transaction = await response.json();
```

### Check transaction

```ts
const response = await fetch(`https://paywithcoin.vercel.app/api/transactions/${code}`);
const transactionChecked = await response.json();
```

## 3. Via curl

### Create transaction

```bash
curl -X POST -H "Content-Type: application/json" -d '{
  "name": "Test name",
  "fiat": {
    "id": "USD",
    "amount": 1
  },
  "crypto_options": [
    {
      "id": "XLM:test",
      "name": "stellar testnet",
      "code": "XLM",
      "address": "GDO6KDYV5RRNJRFZEPYUTFTBMTGQOWCBDB2OZ74EWV32BHXKX6KTNHHA"
    }
  ]
}' https://paywithcoin.vercel.app/api/transactions
```

### Check transaction

```bash
curl https://paywithcoin.vercel.app/api/transactions/<code>
```
