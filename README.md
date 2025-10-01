# Contentstack Kickstart for Veda: The Revival Collection

An upscale unisex jewelry line featuring four distinct sets inspired by early 2000s pop culture, each reinterpreted with modern, understated luxury. Every piece is crafted in combinations of silver, gold, and diamonds, blending youthful nostalgia with refined elegance. Designed to be worn by anyone (cis, trans, or nonbinary), these accessories celebrate the spirit of the 2000s in a contemporary, inclusive aesthetic.

[![Join us on Discord](https://img.shields.io/badge/Join%20Our%20Discord-7289da.svg?style=flat&logo=discord&logoColor=%23fff)](https://community.contentstack.com)

## How to get started

Before you can run this code, you will need a Contentstack "Stack" to connect to.
Follow the following steps to seed a Stack that this codebase understands.

### Install the CLI

```bash
npm install -g @contentstack/cli

# or

npx @contentstack/cli
```

#### Using the CLI for the first time?

It might ask you to set your default region.
You can get all regions and their codes [here](https://www.contentstack.com/docs/developers/cli/configure-regions-in-the-cli) or run `csdx config:get:region`.

> Beware, Free Contentstack developer accounts are bound to the EU region. We still use the CDN the API is lightning fast.

Set your region like so:

```bash
csdx config:set:region EU
```

### Log in via the CLI

```bash
csdx auth:login
```

### Get your organization UID

In your Contentstack Organization dashboard find `Org admin` and copy your Organization ID (Example: `blt481c598b0d8352d9`).

### Create a new stack

Make sure to replace `<YOUR_ORG_ID>` with your actual Organization ID and run the below.

```bash
csdx cm:stacks:seed --repo "contentstack/kickstart-veda-seed" --org "<YOUR_ORG_ID>" -n "Veda: The Revival Collection"
```

## Create a new delivery token.

Go to `Settings > Tokens` and create a delivery token. Select the `development` scope and turn on `Create preview token`

## Fill out your .env file.

Now that you have a delivery token, you can fill out the .env file in your codebase.

> You can find the API key, Delivery Token and Preview Token in Settings > Tokens > Your token.

```
NEXT_PUBLIC_CONTENTSTACK_API_KEY=<YOUR_API_KEY>
NEXT_PUBLIC_CONTENTSTACK_DELIVERY_TOKEN=<YOUR_DELIVERY_TOKEN>
NEXT_PUBLIC_CONTENTSTACK_PREVIEW_TOKEN=<YOUR_PREVIEW_TOKEN>
NEXT_PUBLIC_CONTENTSTACK_REGION=EU
NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT=preview
NEXT_PUBLIC_CONTENTSTACK_PREVIEW=true
```

## Turn on Live Preview

Go to Settings > Live Preview. Click enable and select the `development` environment in the drop down. Hit save.

## Install the dependencies

```bash
npm install
```

### Run your app

```bash
npm run dev
```

### See your page visually

### In the browser

Go to `http://localhost:3000`.

#### In the CMS

Go to Entries and select the only entry in the list.
In the sidebar, click on the live preview icon.
Or, see your entry in the visual builder
