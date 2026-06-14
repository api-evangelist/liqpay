# LiqPay

LiqPay is a Ukrainian payment platform operated by PrivatBank that provides REST APIs for accepting card payments, creating hosted payment pages, processing subscriptions, managing refunds, sending invoices, and conducting card-to-card transfers. It supports Mastercard, Visa, Apple Pay, Google Pay, and Privat24 wallets across 120+ countries, with full fiscalization (RRO) support for Ukrainian merchants.

## APIs

- **Checkout API** — Generate signed payment requests for the hosted LiqPay checkout page
- **Payment Status API** — Look up the current status and details of any transaction
- **Subscriptions API** — Create and manage recurring billing on daily, weekly, monthly, or yearly cycles
- **Refunds API** — Issue full or partial refunds on completed payments
- **Invoice API** — Generate and send itemized invoices to customers by email or phone
- **P2P Transfers API** — Card-to-card money transfers between individuals
- **Payouts API** — Merchant-initiated disbursements to customer cards or accounts
- **Webhooks / Callbacks** — Event-driven server-to-server notifications for payment outcomes
- **Payment Archive API** — Retrieve historical payment records for reconciliation and reporting

## Authentication

All API requests use signature-based authentication:

1. Build a JSON payload with the required parameters including your `public_key`
2. Base64-encode the JSON payload as `data`
3. Generate a SHA-1 HMAC: `base64(sha1(private_key + data + private_key))`
4. POST `data` and `signature` to the API endpoint

Never expose your `private_key` in client-side code.

## Base URLs

| Purpose | URL |
|---------|-----|
| Server-to-server API | `https://www.liqpay.ua/api/request` |
| Client checkout redirect | `https://www.liqpay.ua/api/3/checkout` |

## SDKs

- PHP: https://github.com/liqpay/sdk-php
- Python: https://github.com/liqpay/sdk-python

## Pricing

- Domestic Ukrainian cards: **0.6%** per transaction
- International cards: **up to 2%** per transaction
- No monthly fees, no setup fees
- High-volume merchants may negotiate reduced rates

## Documentation

https://www.liqpay.ua/documentation/en

## Support

- Email: liqpay.support@privatbank.ua
- Portal: https://www.liqpay.ua/en/support
