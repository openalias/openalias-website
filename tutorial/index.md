---
layout: page
title: "How to Add OpenAlias Records"
---

Adding OpenAlias records is easy! Follow these simple steps to add your first OpenAlias v2 record! This is meant to be a user-friendly, interactive tutorial. If you are an expert, skip to the [full specification](https://github.com/openalias/openalias-spec).

## You Should Already Have a Domain Name

This guide assumes that you already have a domain name, and that you can modify TXT records for this domain name. If you do not have a domain yet, you can purchase one from your preferred registrar, such as Cloudflare, GoDaddy, Squarespace, and others.

**In this example, we will add records for a person named Satoshi Nakamoto, with a domain name openalias.org, and an email address satoshi@openalias.org. Replace these with your own details throughout this example!**.

## Add a Name

Let's start by adding your first piece of metadata, your name! This can be your real name or pseudonym, your choice! You can also skip this step.

Create a TXT record with the following name:

`_openalias-metadata.satoshi`

and with the following content:

`oa2 name=Satoshi Nakamoto;`

[![Metadata Name Example](/img/tutorial/Metadata-Name-Example.png){:width="100%"}](/img/tutorial/Metadata-Name-Example.png)

We used "_openalias_metadata.satoshi" as the name since "satoshi" is the subdomain that we wish to assign the record to. Replace "satoshi" with your own preferred subdomain, for example your first name. Replace the portion after "name=" in the content with your name record.

You may choose to add additional items in the content following the semicolon, including the following:

* description
* image (Must be on the same subdomain as the OpenAlias record)
* twitter (Intended for a Twitter/X username, e.g. "AP" (excludes the @))
* nostr (Intended for a Nostr username)
* signal (Intended for a Signal messenger username)

Developers may suggest that you add their own custom items here, depending on their intended use-case for OpenAlias.

If you wish to add items after the name, separate them as such:

`oa2 name=Satoshi Nakamoto; image=https://satoshi.openalias.org/image.png;`

## Add a Bitcoin Address

Adding addresses with OpenAlias is easy. With OpenAlias v2, there are many more optional features than there were with OpenAlias v1.

Create a TXT record with the following name:

`openalias-payment.satoshi`

and with the following content:

`oa2 btc/btc address=1FhnVJi2V1k4MqXm2nHoEbY5LV7FPai7bb;`

Obviously, you should replace the address above with your own!

[![Metadata Address Example 1](/img/tutorial/Metadata-Address-Example-1.png){:width="100%"}](/img/tutorial/Metadata-Address-Example-1.png)

### Specify Address Type

The record above will work, but let's explore one new feature of OpenAlias v2: specifying address types! This allows you to add *multiple* records for a single asset type, and the sending wallet can pick the most compatible among the available options.

Using the same address as before, we can append "p2pkh/" in front of the address like so:

`oa2 btc/btc address=p2pkh/1FhnVJi2V1k4MqXm2nHoEbY5LV7FPai7bb;`

Then, we can make a new address record with the following name (the same one):

`openalias-payment.satoshi`

and with the following content:

`oa2 btc/btc address=bip352/sp1qqfk0ag4gmq87agdy8lawrlt2mf3p8myhkuxgp5s7kdck4ywwg7mjjqc2wmmtfddvevmjnlv4klmgsx4g79rr998d20r5vmxera5f2a54nu5h496v;`

[![Metadata Address Example 2](/img/tutorial/Metadata-Address-Example-2.png){:width="100%"}](/img/tutorial/Metadata-Address-Example-2.png)

We now have *both* a legacy Bitcoin p2pkh address *and* a Bitcoin Silent Payments address added to our username! You can repeat this for other address types you wish to add, and for additional assets you wish to add.

## Adding Other Assets

Replace "btc/btc" with the correct OpenAlias asset identifer. Use [this network/blockchain table](https://github.com/openalias/openalias-spec/blob/main/oa2-lists/asset_network.csv) and [this asset table](https://github.com/openalias/openalias-spec/blob/main/oa2-lists/asset_type.csv) for the full list of supported networks and assets. Some common ones are below:

* xmr/xmr (Monero)
* ltc/ltc (Litecoin)
* eth/usdc (USD Coin on Ethereum)
* trx/usdt (Tether USD on Tron)

## Optional: Adding Priorities

You can specify which network you prefer to receive a given asset on. This is an advanced feature. If you want to keep things basic, then only add one record for each asset and use your preferred network.

Suppose that we prefer to receive USDT on Polygon, but that we also will accept USDT on Ethereum. We will create two records

Create the first TXT record with the following name:

`_openalias-routing.satoshi`

and with the following content:

`oa2 poly/usdt 10`

Create the second TXT record with the following name (the same one):

`_openalias-routing.satoshi`

and with the following content:

`oa2 eth/usdt 20`

With these two new records, we have indicated that we prefer (because we have assigned a *lower number*, or a *higher priority*) to receive USDT on Polygon, though we will also accept USDT on Ethereum.

Keep in mind that for OpenAlias priority records to work, you need existing "openalias-payment" records for the network and asset type.

## Full Specification

Available here: [https://github.com/openalias/openalias-spec](https://github.com/openalias/openalias-spec)

## Legacy OpenAlias V1 Record

You may wish to add a legacy OpenAlias v1 record. OpenAlias v1 only focused on addresses, and any metadata was added to the address record directly instead of assigned to a separate metadata folder like in v2. OpenAlias v1 records are easily added as follows:

> oa1:<asset_ticker> recipient_address=<address>; recipient_name=<name>

One example record is shown below:

> oa1:xmr recipient_address=46BeWrHpwXmHDpDEUmZBWZfoQpdc6HaERCNmx1pEYL2rAcuwufPN9rXHHtyUA4QVy66qeFQkn6sfK8aHYjA3jk3o1Bv16em; recipient_name=Monero Development;

OpenAlias v1 did not maintain a list of asset_ticker names. However, the most commonly used asset_tickers for v1 include the following:

* xmr (Monero)
* btc (Bitcoin)
* ltc (Litecoin)

You can optionally provide additional key-value pairs for the following:

* tx_description
* tx_amount
* tx_payment_id
* address_signature
* checksum

## Help Us Improve

Please let us know how we can improve this tutorial!
