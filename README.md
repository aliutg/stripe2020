# Product Management Take-Home Assignment 
Anna Liu, May 2020

## Accept payments with Stripe Checkout (React client-only)

This is a React version of the HTML + Vanilla JavaScript client implementation. It works with any of the backends in the `server` folder.

## Setup

- Create a React App by following the directions at https://create-react-app.dev/docs/getting-started/
- Manually clone and configure this assignment:

```bash
git clone https://github.com/all819/stripe2020
```

- Enable client-only checkout: https://dashboard.stripe.com/account/checkout/settings
- Create a one-time or recurring product in the Stripe Dashboard: https://dashboard.stripe.com/products
  - After creation click the "Use with checkout" button and copy the sku (sku_xxx) ID.
- Navigate into checkout-one-time-payments/client
- Set up the environment variables for React:

```bash
cp .env.example .env
```

In the newly created `.env` file, set the values:

- Set the sku ID that you created in the Dashboard for `REACT_APP_SKU_ID`
- Copy your publishable key from: https://dashboard.stripe.com/apikeys and set it as the value for `REACT_APP_STRIPE_PUBLISHABLE_KEY`
- Set `REACT_APP_BASE_PRICE` and `REACT_APP_CURRENCY` to match your sku details from the Dashboard

## How to run

1. Install the dependecies:

```bash
npm install
```

2. Start the React client:

```bash
npm start
```

- Client running on http://localhost:3000

## Track successful payments

- Set up the Stripe CLI by following the steps at https://stripe.com/docs/stripe-cli
- Link your Stripe account by following the steps at https://stripe.com/docs/stripe-cli#link-account
- Generate your webhook secret key:

```bash
stripe listen
```

The CLI will print a webhook secret key to the console. Set REACT_APP_STRIPE_WEBHOOK_SECRET to this value in your .env file.

You should see events logged in the console where the CLI is running.
- Log the events in a locally stored file:

```bash
stripe listen --events=payment_intent.succeeded >> log.txt
```

## Credits

- Author: [@all819]
- Heavily copied from stripe-samples/checkout-one-time-payments
- This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).
