# Accept YooKassa payments and log transactions in Google Sheets

## 🧾 Summary

This workflow allows you to accept online payments via **YooKassa** and log both orders and transactions in **Google Sheets** — all without writing a single line of code. It supports full payment flow: product selection, payment initiation, webhook processing, refund updates, and payment status checks.

---

## 👥 Who is this for?

This template is ideal for:

* Online stores with simple checkout flows
* Sellers of digital products or info-courses
* Entrepreneurs using Telegram bots or web forms
* Anyone needing quick payment integration with Google Sheets tracking

---

## 🎯 What problem does this workflow solve?

Setting up online payments usually requires backend infrastructure. This no-code solution automates the entire payment flow:

* Handles product listing and price retrieval
* Initiates payments with email and return URL
* Listens for `payment.succeeded` and `refund.succeeded` events
* Records every action into structured Google Sheets

---

## ⚙️ What this workflow does

### 1. **GET /products**

Returns a sorted list of products from a Google Sheet (`products`).

### 2. **POST /payment**

* Validates required fields (`product_id`, `email`, `return_url`)
* Checks email format
* Fetches product data from `products`
* Generates a unique idempotence key
* Sends a request to YooKassa API
* Saves the order into the `orders` sheet
* Returns a payment confirmation link

### 3. **POST /yoomoney**

Webhook to process payment/refund events:

* On `payment.succeeded`, adds entry to `transactions`
* On `refund.succeeded`, updates transaction status

### 4. **GET /status/\:id**

Returns real-time payment status from YooKassa

---

## 🚀 Setup

1. **Connect credentials:**

   * Google Sheets (OAuth2)
   * YooKassa (Basic Auth using `shopId` and `secretKey`)

2. **Update the following Google Sheets:**

   * `products`: should contain `product_id`, `title`, `price`
   * `orders`: for saving confirmed purchases
   * `transactions`: for logging all successful or refunded payments

3. **Test endpoints using any HTTP client**:

Example payload for `/payment`:

```json
{
  "product_id": "abc123",
  "email": "user@example.com",
  "return_url": "https://your.site/success"
}
```

---

## 🔧 How to customize this workflow

* Add delivery logic (e.g., email with product link after successful payment)
* Replace Google Sheets with a database (e.g., PostgreSQL)
* Connect Telegram or other messengers for post-payment notifications
* Add promo codes, discounts, or subscriptions logic

---

## 💼 Use cases

* Simple online checkouts
* Telegram bots selling access
* Educational product sales
* MVP e-commerce flows
* Donation or membership payments

---

## 📎 Notes

✅ Includes Sticky Notes for sections
✅ Includes error handling and validation
✅ No custom code needed except UUID generation
