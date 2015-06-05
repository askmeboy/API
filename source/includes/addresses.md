# Addresses

## Get Addresses

```shell
curl "http://127.0.0.1:9085/addresses"
```

```http
GET addresses HTTP/1.1
Host: 127.0.0.1:9085
```

Returns an array of all the addresses in your wallet.

### REQUEST

`GET addresses`

<aside class="notice">
You can execute this command by clicking here: <a href="http://127.0.0.1:9085/addresses" target="blank">http://127.0.0.1:9085/addresses</a>
</aside>

### Errors

| Error | Description |
| --- | --- |
| 201 | Wallet does not exist. |

## Validate Address

```shell
curl "http://127.0.0.1:9085/addresses/validate/{address}"
```

```http
GET addresses/validate/{address} HTTP/1.1
host: 127.0.0.1:9085
```
Validates the given address.Returns true/false.

### REQUEST

`GET addresses/validate/{address}`

## Get Address Seed

```shell
curl "http://127.0.0.1:9085/addresses/seed/{address}"
```

```http
GET addresses/seed/{address} HTTP/1.1
Host: 127.0.0.1:9085
```
Returns the 32-byte long base58-encoded account seed of the given address.

### REQUEST

`GET addresses/seed/{address}`

### Errors

| Error | Description |
| --- | --- |
| 102 | Invalid address. |
| 201 | Wallet does not exist. |
| 202 | Address does not exist in wallet. |
| 203 | Wallet is locked. |

## Create A New Address

```shell
curl "http://127.0.0.1:9085/addresses/new"
```

```http
GET addresses/new HTTP/1.1
Host: 127.0.0.1:9085
```

Generates a new account and returns the newly generated address.

### REQUEST

`GET addresses/new`

### Errors

| Error | Description |
| --- | --- |
| 201 | Wallet does not exist. |
| 203 | Wallet is locked. |



## Import Address

```shell
curl "http://127.0.0.1:9085/addresses"
  -X POST
  -d seed
```

```http
POST addresses HTTP/1.1
Host: 127.0.0.1:9085
seed
```

Imports the given 32-byte long base58-encoded account seed.

Returns the address when successfully imported.

### REQUEST

`POST addresses seed`

### Errors

| Error | Description |
| --- | --- |
| 103 | Invalid seed. |
| 201 | Wallet does not exist. |
| 203 | Wallet is locked. |

## Delete Address

```shell
curl "http://127.0.0.1:9085/addresses/{address}
  -X DELETE
```

```http
DELETE addresses/{address} HTTP/1.1
Host: 127.0.0.1:9085

```
Deletes the given address.Returns true/false.

### REQUEST

`DELETE addresses/{address}`

### Errors

| Error | Description |
| --- | --- |
| 102 | Invalid address. |
| 201 | Wallet does not exist. |
| 203 | Wallet is locked. |

## Get Address Balance

```shell
curl "http://127.0.0.1:9085/addresses/balance/{address}"
```

```http
GET addresses/balance/{address} HTTP/1.1
Host: 127.0.0.1:9085
```

Returns the confirmed balance of the given address.

### REQUEST

`GET addresses/balance/{address}`

### Errors

| Error | Description |
| --- | --- |
| 102 | Invalid address. |

## GET Address Generating Balance

```shell
curl "http://127.0.0.1:9085/addresses/generatingbalance/{address}"
```

```http
GET addresses/generatingbalance/{address} HTTP/1.1
Host: 127.0.0.1:9085
```

Return the generating balance of the given address.

### REQUEST

`GET addresses/generatingbalance/{address}`

## GET addresses/assetbalance/{assetid}/{address}

```shell
GET addresses/assetbalance/{assetid}/{address}
```

Returns the confirmed balance of the given asset ID and the given address.

### Errors

| Error | Description |
| --- | --- |
| 102 | Invalid address. |
| 601 | Invalid asset id. |

## GET addresses/balance/{address}/{confirmation}

```shell
GET addresses/balance/{address}/{confirmation}
```

Calculates the balance of the given address after the given confirmations.

0 confirmations can only be used on addresses that exist in your wallet.

### Errors

| Error | Description |
| --- | --- |
| 102 | Invalid address. |

## GET addresses/publickey/{address}
```shell
GET addresses/publickey/{address}
```

Returns the public key of the given address

###

| Error | Description |
| --- | --- |
| 102 | Invalid address. |

## POST addresses/sign/{address}

```shell
POST addresses/sign/{address}
```

Signs the  given message using the given address.

> Format

```json
{
  "message": "test",
  "publickey": "6cWtyccawscvHhE5woPaLbDUc6qFaH7b7YuDJFrBvgJ3",
  "signature": "2XuAEoUG2GmWJ8s5ZMZMK7csQ1nfHcqL5JYm3JBqetUAZKeT9mu7mSKYYMjLQoLBr5DqLCfaKXLQJnbzCLYCfC21"
}
```
### Errors

| Error | Description |
| --- | --- |
| 102 | Invalid address. |
| 201 | Wallet does not exist. |
| 202 | Address does not exist in wallet. |
| 203 | Wallet is locked. |

## POST addresses/verify/{address}

```shell
POST addresses/verify/{address}
```

Verifies if the given message was signed by the given address. Returns true/false.

> Format

```json
{
  "message": "test",
  "publickey": "6cWtyccawscvHhE5woPaLbDUc6qFaH7b7YuDJFrBvgJ3",
  "signature": "2XuAEoUG2GmWJ8s5ZMZMK7csQ1nfHcqL5JYm3JBqetUAZKeT9mu7mSKYYMjLQoLBr5DqLCfaKXLQJnbzCLYCfC21"
}
```
### Errors

| Error | Description |
| --- | --- |
| 101 | Invalid signature |
| 102 | Invalid address. |
| 112 | Invalid public key. |