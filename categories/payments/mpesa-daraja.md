# MPESA Daraja API

**Description**:  
The MPESA Daraja API allows developers to integrate M-PESA payment processing capabilities into their applications. It offers several services, including STK Push, C2B (Customer to Business), B2C (Business to Customer), and B2B (Business to Business) transactions, as well as checking transaction statuses.

**Authentication**:  
Requires an API key, Consumer Key, and Consumer Secret. You can obtain these by signing up on the [Safaricom Developer Portal](https://developer.safaricom.co.ke/).

**Base URL**:  
`https://sandbox.safaricom.co.ke/` - **Sandbox environment**
`https://api.safaricom.co.ke/` - **Production environment**

---

## Endpoints

### 1. **STK Push (Lipa na M-PESA Online Payment)**

- **Endpoint**: `/mpesa/stkpush/v1/processrequest`
- **Description**: Initiates an M-PESA payment on behalf of a customer by sending a payment prompt to their mobile phone.
  
- **Parameters**:
    - `BusinessShortCode`: The organization shortcode used to receive the transaction.
    - `Password`: Base64 encoded string of the BusinessShortCode, Lipa Na M-PESA Passkey, and Timestamp.
    - `Timestamp`: The timestamp of the transaction in the format `yyyyMMddHHmmss`.
    - `TransactionType`: The type of transaction (e.g., `CustomerPayBillOnline`).
    - `Amount`: The amount to be transacted.
    - `PartyA`: The MSISDN sending the funds.
    - `PartyB`: The organization shortcode receiving the funds.
    - `PhoneNumber`: The MSISDN sending the funds.
    - `CallBackURL`: The URL to receive the result of the transaction.
    - `AccountReference`: The account reference for the transaction.
    - `TransactionDesc`: The description of the transaction.


- **Example Request**:
```bash
curl -X POST "https://sandbox.safaricom.co.ke/mpesa/stkpush/v1/processrequest" \
-H "Authorization: Bearer ACCESS_TOKEN" \
-H "Content-Type: application/json" \
-d '{
  "BusinessShortCode": "174379",
  "Password": "YOUR_BASE64_ENCODED_PASSWORD",
  "Timestamp": "20211012121530",
  "TransactionType": "CustomerPayBillOnline",
  "Amount": "10",
  "PartyA": "254708374149",
  "PartyB": "174379",
  "PhoneNumber": "254708374149",
  "CallBackURL": "https://example.com/callback",
  "AccountReference": "INV001",
  "TransactionDesc": "Payment for goods"
}'

```

- **Example Response**:
```json
{
  "MerchantRequestID": "19465-780693-1",
  "CheckoutRequestID": "ws_CO_27072021084047716",
  "ResponseCode": "0",
  "ResponseDescription": "Success. Request accepted for     processing",
  "CustomerMessage": "Success. Request accepted for processing"
}

```

### 2. **Transaction Status Request**

- **Endpoint**: `/mpesa/transactionstatus/v1/query`
- **Description**: Checks the status of a specific transaction.
- **Parameters**:
    - `Initiator`: The name of the initiator.
    - `SecurityCredential`: The base64-encoded security credential.
    - `CommandID`: The command ID (e.g., `TransactionStatusQuery`).
    - `TransactionID`: The unique M-PESA transaction ID.
    - `PartyA`: The MSISDN sending the funds.
    - `IdentifierType`: The type of the identifier (e.g., `4` for MSISDN).
    - `ResultURL`: The URL to receive the result of the transaction.
    - `QueueTimeOutURL`: The URL to receive the result of the transaction.
    - `Remarks`: Additional remarks.
    - `Occasion`: The occasion for the transaction.


- **Example Request**:
```bash
curl -X POST "https://sandbox.safaricom.co.ke/mpesa/transactionstatus/v1/query" \
-H "Authorization: Bearer ACCESS_TOKEN" \
-H "Content-Type: application/json" \
-d '{
  "Initiator": "testapi",
  "SecurityCredential": "YOUR_SECURITY_CREDENTIAL",
  "CommandID": "TransactionStatusQuery",
  "TransactionID": "LKXXXX1234",
  "PartyA": "600XXX",
  "IdentifierType": "4",
  "ResultURL": "https://example.com/callback",
  "QueueTimeOutURL": "https://example.com/timeout",
  "Remarks": "Checking transaction status",
  "Occasion": ""
}'
```

- **Example Response**:
```json
{
  "ConversationID": "AG_20211012_00004a1d",
  "OriginatorConversationID": "19465-780693-1",
  "ResponseCode": "0",
  "ResponseDescription": "The service request is processed successfully."
}
```

### 3. **C2B (Customer to Business Payment)**

- **Endpoint**: `/mpesa/c2b/v1/simulate`
- **Description**: Simulates a C2B payment, typically used for testing M-PESA PayBill or Buy Goods.
- **Parameters**:
    - `ShortCode`: The organization shortcode used to receive the transaction.
    - `CommandID`: The command ID (e.g., `CustomerPayBillOnline`).
    - `Amount`: The amount to be transacted.
    - `Msisdn`: The MSISDN sending the funds.
    - `BillRefNumber`: The bill reference number for the transaction.

- **Example Request**:
```bash
curl -X POST "https://sandbox.safaricom.co.ke/mpesa/c2b/v1/simulate" \
-H "Authorization: Bearer ACCESS_TOKEN" \
-H "Content-Type: application/json" \
-d '{
  "ShortCode": "600XXX",
  "CommandID": "CustomerPayBillOnline",
  "Amount": "100",
  "Msisdn": "254708374149",
  "BillRefNumber": "INV001"
}'
```

- **Example Response**:
```json
{
  "ConversationID": "AG_20211012_00005a4d",
  "OriginatorConversationID": "19466-780693-1",
  "ResponseCode": "0",
  "ResponseDescription": "Accept the service request successfully."
}
```

## Rate Limits
- **Sandbox**: 5 requests per second
- **Production**: 10 requests per second

## Resources
- [Documentation](https://developer.safaricom.co.ke/Documentation)
- [Safaricom Developer Portal](https://developer.safaricom.co.ke/)