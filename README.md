<img src="./images/primer-banner.png"  width="100%"/>

<h1 align="center"><img src="./images/primer-logo.png" height="24px"> Example Web Checkout</h1>

<h3 align="center">

Example integration of Universal Checkout using the [Primer Web SDK](https://primer.io)

</h3>

<h4 align="center">

This is a companion project to the [Web Getting Start Guide](https://primer.io/docs/get-started/web).

</h4>

---

## 📝 About This Implementation

This project is a **clone** of the official Primer example repository: [https://github.com/primer-io/example-web-checkout](https://github.com/primer-io/example-web-checkout)

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

### Assumptions Made

- The user has a valid Primer Sandbox account with API access
- The API key provided in `.env` matches the Sandbox environment
- The checkout will be used for testing purposes only (Sandbox mode)
- Node.js and npm/yarn are available on the development machine
- Port 8880 is available for local development (configurable via `PORT` env variable)

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

## 👀 What's next?

- ✨ Explore the capabilities of your [Dashboard](https://dashboard.sandbox.primer.io/)
- 📚 Take a look at our [Documentation](https://primer.io/docs) to customize Universal Checkout to better fit your needs
- 📖 Explore our [Web SDK Reference](https://www.npmjs.com/package/@primer-io/checkout-web) and [Server API Reference](https://apiref.primer.io)
- 🎒 Learn more about [how Primer works](https://primer.io/docs/how-primer-works)
- 🤙 Reach out to us at [support@primer.io](mailto:support@primer.io) if you are facing any issues
- 🤘 Join our developer community on [Discord](https://bit.ly/3xBTFl6)
