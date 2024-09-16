---
layout: page
title: "About"
---

## What is OpenAlias?

OpenAlias seeks to provide a way to simplify aliasing amidst a rapidly shifting technology climate. Users are trying to cross the bridge to private and cryptographically secure infrastructure and systems, but many of them have just barely started remembering the email addresses of their friends and family.

As part of the ongoing development of the [Monero cryptocurrency project](https://getmonero.org/), we asked ourselves: how can we simplify payments for users unfamiliar with cryptocurrency? Monero stealth addresses are at least 95 characters long - memorising them is not an option, and asking someone to send a payment to <95-character-string> is only going to lead to confusion.

At its most basic, OpenAlias is a TXT DNS record on a FQDN (fully qualified domain name). By combining this with DNS-related technologies we have created an aliasing standard that is extensible for developers, intuitive and familiar for users, and can interoperate with both centralised and decentralised domain systems.

## How is it superior to other aliasing systems?

Typical aliasing systems are simple key-value stores. A cryptocurrency may, for instance, have an aliasing system that lets you (through the process of mining) declare that the alias Bob is equal to <95-character-string>. This has two major pitfalls for end-users. Firstly, it makes it the responsibility of that cryptocurrency to resolve issues or alias disputes. For instance, if a user loses their private keys and want to continue using that alias, there needs to be a mechanism in place for that, otherwise you end up with dead aliases and users have the hassle of having to update everyone that they have a new alias. The second problem is that it doesn't actually solve anything. Once the first few Bob-derived aliases are taken, users end up resorting to things like Bob1979-awesomesauce324, which means that the end-user still has to have that written down in an address book somewhere.

## Who created OpenAlias?

The idea of a DNS-based alias system is not new, and has been suggested on more than one occassion. The groundwork for OpenAlias was initially done by Riccardo "fluffypony" Spagni and Naphex, formerly of btcXchange.ro. Many months after this initial gem of an idea was born Riccardo, along with the rest of the Monero core team, fleshed it out into a practical and extensible standard. A special thanks goes to Tom Winget, who created the first OpenAlias client implementation in Monero Core.

## What OpenAlias implementations exist?

The Monero core team, and other contributors, are actively adding new OpenAlias implementations. To that end, there are currently these implementations:

* [Electrum, lightweight Bitcoin wallet](https://electrum.org/) (from 2.0 onwards)
* [MyMonero, a web-based Monero account/wallet management system](https://mymonero.com/)
* [Monero Core, including the simplewallet and rpcwallet applications](https://getmonero.org/)
* [Coin.Space, a web-based Bitcoin and Litecoin wallet](https://coin.space/)
* [openalias.rs, a command-line tool and Rust library for looking up and parsing OpenAliases](https://github.com/nabijaczleweli/openalias.rs)
* [Cake Wallet, a multi-cryptocurrency self-custody wallet](https://cakewallet.com)
* [Monerujo, an Android Monero self-custody wallet](https://www.monerujo.io/)
* [Feather Wallet, a desktop Monero self-custody wallet](https://featherwallet.org/)
