## Transfers

### Create transfers from payment
```php
$api->payment->fetch($paymentId)->transfer(array('transfers'=>array(array('account' => $accountId, 'amount' => 100, 'currency' => 'INR'))));
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| paymentId*   | string      | The id of the payment to be fetched         |
| transfers*    | array       | Details regarding the transfer.   |

-------------------------------------------------------------------------------------------------------

### Fetch transfer for an order
```php
$api->order->fetch($orderId)->transfers(array('expand[]'=>'transfers'));
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| orderId*   | string      | The id of the order to be fetched  |
| expand*   | string    | Supported value is `transfer`  |

-------------------------------------------------------------------------------------------------------

### Fetch transfer
```php
$api->transfer->fetch($transferId);
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| transferId*   | string      | The id of the transfer to be fetched  |

-------------------------------------------------------------------------------------------------------

### Fetch transfers for a settlement
```php
$api->transfer->all(array('recipient_settlement_id'=> $settlementId));
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| settlementId*   | string    | The id obtained from the settlement.processed webhook payload.  |

-------------------------------------------------------------------------------------------------------

### Fetch settlement details
```php
$$api->transfer->all(array('expand[]'=> 'recipient_settlement'));
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| expand*   | string    | Supported value is `recipient_settlement`  |

-------------------------------------------------------------------------------------------------------

### Reverse transfers from all linked accounts
```php
$api->transfer->fetch($transferId)->reverse(array('amount'=>'100'));
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| transferId*   | string      | The id of the transfer to be fetched  |
| amount   | integer      | The amount to be captured (should be equal to the authorized amount, in paise) |

-------------------------------------------------------------------------------------------------------

### Direct transfers
```php
$api->transfer->create(array('account' => $accountId, 'amount' => 500, 'currency' => 'INR'));
```

**Parameters:**

| Name          | Type        | Description                                 |
|---------------|-------------|---------------------------------------------|
| accountId*   | string      | The id of the account to be fetched  |
| amount   | integer      | The amount to be captured (should be equal to the authorized amount, in paise) |
| currency   | string  | The currency of the payment (defaults to INR)                                  |

-------------------------------------------------------------------------------------------------------

**PN: * indicates mandatory fields**
<br>
<br>
**For reference click [here](https://razorpay.com/docs/api/route/#transfers/)**