# Intro

## How it works

![Schema how service works](/static/how-work.svg)

### A scenario explanation

1. A user visits your site and decides to buy something with crypto.
2. You create a transaction for a payment, setting the amount in both fiat and cryptocurrency.
3. You redirect the user to the payment widget to display payment information and allow the user to interact with the transaction.
4. The user selects crypto for payment and transfers coins.
5. Our service checks the transfer to your wallet to finalize the transaction.
6. You check the transaction status in our service.

## Stages of payment widget

- New: The transaction was created.
- Updated: The user selects a cryptocurrency. At the moment of selection, the service saves the current cryptocurrency exchange rate for the transaction. From this moment, the user knows how much to pay.
- Finished/Failed: The transaction is completed.

### Limits

- A new transaction has an expiration time. During that time, the user should select a cryptocurrency and update the transaction. You can control it with the field `time_to_update` in the transaction. By default, this time is 2.5 hours.
- An updated transaction has an expiration time. The user should transfer enough coins to the wallet within a certain time. You can control it with the field `time_to_pay` in the transaction. By default, this time is 6 hours.
