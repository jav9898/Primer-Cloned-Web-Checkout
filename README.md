<img src="./images/primer-banner.png"  width="100%"/>

<h1 align="center"><img src="./images/primer-logo.png" height="24px"> Example Web Checkout</h1>

---

## About This Implementation

DISCLAIMER
This project is a **clone** of the official Primer example repository: [Primer Web Checkout](https://github.com/primer-io/example-web-checkout)

### Modifications Made

The following changes were made to adapt this integration for local testing and to use updated API versions:

- **API Version Update**: Updated from `X-Api-Version: 2.2` to `X-Api-Version: 2.4` to use the latest API version
- **Currency Change**: Changed from `EUR` to `SGD` (Singapore Dollars) for regional testing
- **Customer Email**: Updated from `test@test.com` to `javier@test.com` for personal testing
- **Payment Amount**: Increased from `2500` (€25.00) to `3000` (SGD 30.00) for the test transaction

### Integration Setup

This implementation follows the Primer Web SDK integration guidelines:

1. **Web SDK Installation**: The checkout uses the Primer Universal Checkout loaded from the CDN
2. **Local Initialization**: The checkout is initialized in a local test environment using the Sandbox API
3. **Checkout Flow**: A simple payment flow demonstrating:
   - Client-side checkout initialization
   - Payment method tokenization
   - Server-side payment authorization
4. **Configuration**: All configurations are managed through environment variables in `.env`

### Challenges Encountered

- **API Version Compatibility**: The original repository used API version 2.2, which has been superseded by version 2.4. This required updating the `X-Api-Version` header to ensure compatibility with the current Primer API.
- **Regional Configuration**: Adapting the currency from EUR to SGD required updating both the `currencyCode` field and ensuring the payment amount was appropriate for the target currency.
- **Environment Setup**: Ensuring the correct API key and environment configuration (SANDBOX vs PRODUCTION) was critical for successful local testing.

<br />

## ✅ Pre-requisites

- **A Primer sandbox account** 🚀

- **A handful of programs installed on your machine** <br /> `node`, and `yarn` or `npm`, that's it! 💪

- **5 minutes of your time** <br /> Then you can show your colleagues how powerful Universal Checkout is 😎

## 🚀 Get Started

### 👨‍💻 Installation

Clone this repository:

```bash
git clone https://github.com/primer-io/example-web-checkout.git
cd ./example-web-checkout
```

Then install the dependencies using `yarn` or `npm`:

```bash
# With yarn
yarn
```

```bash
# With npm
npm i
```

### 🔑 Set up the API Key

Grab your API Key, or create a new one, from the [Primer Dashboard](https://sandbox-dashboard.primer.io/developers/apiKeys).

![Dashboard API Key](./images/apikey.png)

Copy `env.example` and name the file `.env`.

```
cp env.example .env
```

Open `.env` and set the environment variable `API_KEY` with the API key available on your dashboard.

```
# .env
API_KEY=1234-1234-1234-1234 # Your Primer API Key
```

### 🏃‍♂️ Run the server

```bash
# With yarn
yarn start

# With npm
npm start
```

The server is deployed on port `8880` by default. You can change the port by setting the `PORT` environment variable in the `.env` file.

This server uses [`nodemon`](https://www.npmjs.com/package/nodemon) under the hood to automatically re-run the server when a change to the source files or `.env` is made.

### 💳 Access the checkout

Check the checkout at [http://localhost:8880/](http://localhost:8880/).

You should see Universal Checkout appear with the payment methods configured on your [Dashboard](https://dashboard.sandbox.primer.io/checkout)! 🎉

![Checkout UI](./images/checkout.png)

## ⚙️ Configuration & Customization

All checkout configuration is managed in the `src/server.js` file. To customize the checkout behavior, edit the `/client-session` endpoint (around line 37).

### Key Configuration Options

**File to edit:** `src/server.js`

#### Currency and Amount
- **Currency Code** (line 53): Change the 3-character currency code
  ```javascript
  currencyCode: 'SGD', // Change to 'USD', 'EUR', etc.
  ```

- **Payment Amount** (line 80): Update the amount in minor units (cents)
  ```javascript
  amount: 3000, // 3000 = $30.00, 2500 = $25.00, etc.
  ```

- **Item Quantity** (line 81): Adjust the quantity of items
  ```javascript
  quantity: 12, // Change to desired quantity
  ```

#### Customer Information
- **Email Address** (line 57): Update customer email
  ```javascript
  emailAddress: "javier@test.com", // Change to your test email
  ```

- **Mobile Number** (line 58): Update customer phone
  ```javascript
  mobileNumber: "+6588889999", // Change to your test number
  ```

- **Customer Name** (lines 59-60): Update customer name
  ```javascript
  firstName: "John",
  lastName: "Smith",
  ```

- **Billing Address** (lines 61-68): Update billing address details
  ```javascript
  billingAddress: {
    firstName: "John",
    lastName: "Smith",
    postalCode: "CB94BQ",
    addressLine1: "47A",
    countryCode: "CL",
    city: "Cambridge",
    state: "Cambridgeshire"
  }
  ```

#### API Version
- **API Version** (line 44): Update if needed for compatibility
  ```javascript
  'X-Api-Version': '2.4', // Current version
  ```

#### Item Details
- **Item ID** (line 78): Product identifier
  ```javascript
  itemId: 'shoes-123', // Change to your product ID
  ```

- **Item Description** (line 79): Product description
  ```javascript
  description: 'Some nice shoes!', // Change to your product description
  ```

### Applying Changes

After making changes to `src/server.js`:
1. Save the file
2. The server will automatically restart (thanks to nodemon)
3. Refresh your browser at http://localhost:8880/ to see the changes

### Environment Variables

For API configuration, edit the `.env` file:
- **API_KEY**: Your Primer API key (required)
- **PRIMER_API_ENVIRONMENT**: Set to `SANDBOX` or `PRODUCTION`
- **PORT**: Server port (default: 8880)