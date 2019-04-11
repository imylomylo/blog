---
id: 441
title: 'RedFOX Labs IEO: why using blockchain components of Komodo to accelerating adoption is a win for everyone'
date: 2019-04-11
author: Mylo Mylo
layout: post
categories:
  - blockchain
  - komodo
  - cryptocurrency
  - redfox
tags: [featured]
---
RedFOX Labs is a start up that creates start ups.  An incubator.  They are seeking funding to bootstrap this incubation process.   The funding drive comes from an IEO tomorrow - April 12.  The focus for this article is written from a technical point of view.  Not a financial point of view.  The technical highlights of Komodo are well known to me, because I have written approximately 30 of the Komodo Tech Tuesday articles to date.  RedFOX CEO Ben Fairbank, colloquially known by his online handle bitcoinbenny, shot me a question for technical resources recently, which I will include in this article.  It may not be clear to people where Komodo's technology fits in the creation of new startups, products and services, so let me try to make things more evident.

Looking at the proposal through their whitepaper, there are three sample apps for the media & finance industries as well as the proof of concept Zaddex hybrid exchange.  The three sample apps are:
* VIETPAY
* VIETFLIX
* InstaNAM

Additionally, the recently created project Komodore64 gaming platform has announced a partnership with RedFOX.

## How can these platforms be built using Komodo?
Whether the platforms created in the future raise their own funds or create their own currencies or tokens, the initial blockchain creation for any project RedFOX Labs undertakes is possible with Komodo's Blockchain Starter Kit (BSK).  This is provided in both technical form (DIY Blockchain) and in service form - through service providers found at the Komodo BSK page.   The Komodo team is also creating a SaaS blockchain generator due for launch Q2 2019.  A custom blockchain is generated with it's own characteristics including rewards, supply, consensus, blocktime and more.  So once these blockchains are created, how do you build on top of them?

### Payment Systems
* Cryptocurrencies & Stablecoins
* Wallet & DEX

The crypto & stablecoin can be created with a new blockchain above.  In the current news cycle, Facebook is hiring blockchain staff and online chatter revolves around a [Facebook stablecoin rumours](https://beincrypto.com/facebook-reportedly-seeking-investors-for-future-stablecoin/).  In week 6 of Komodo's tech tuesday, I compared [Facebook crypto acquisition to Komodo](https://komodoplatform.com/tt2019-6-facebook-crypto-comparison-erc20-migrations/).

There is a new wallet in closed-alpha testing at the moment written from scratch and developed mobile-first.  It's a [crypto-superwallet actively tested](https://twitter.com/0xca333/status/1113045156826136576).  Multi-coin with a DEX baked in.  RedFOX also partners with Zaddex, the hybrid DEX/CEX exchange.  The RedFOX team has not disclosed the development roadmap of their payment system - I am only highlighting what Komodo technology is available to create a payment platform that accepts multi-currency.

Komodo has provided a whitelabel multi-currency wallet since 2017.  The often criticized Agama wallet with it's "clunky" look and feel can be made beautiful.

### Streaming Services
There are already a couple of blockchain integrated streaming media services - namely DTube amongst others.  In Komodo's Tech Tuesday #6 from 2018, I wrote about the [blockchain streamer proof of concept](https://komodoplatform.com/tech-tuesday-update-6/).  What hasn't been recorded anywhere unfortunately is the proof of concept I quickly made for capturing webcam data using the browser's getUserMedia capabilities.  [Capturing video chunks around this line of code](https://github.com/imylomylo/samples/blob/gh-pages/src/content/getusermedia/record/js/main.js#L76) and appending to the local array of chunks, was instead fired off to the local running streaming transaction instance.

Given my testing was for live streaming, the Tech Tuesday article was for an existing data file - the likely solution for a VIETFLIX type of service.

### Photo Media Services
There is more than one way to architect a photo media service.  Whether it is with a URL (web or IPFS) or whether it is stored on the blockchain, like using an oracle for [industry certifications storage](https://komodoplatform.com/tt2019-5-peer-to-peer-orderbooks-first-atomic-swap/) there are many ways to develop it.  More importantly, evolving the service as product life-cycles change or as the technology adoption grows - Komodo can adapt via it's multi-chain architecture and the ability to migrate chain data.  Interestingly, if decentralized control of your own data leads to payments to the content creator via streaming payments or micro-transactions via [on-chain instant channel payments](https://komodoplatform.com/tech-tuesday-update-2/).
Komodo can mix-and-match it's technology offerings to cater for business requirements.  It also scales because of the multi-chain architecture.

### Komodore64 Gaming Platform Partnership

## Why does RedFOX success benefit everyone?
Komodo is an open ecosystem.  RedFOX is the first incubation project attempting to take Komodo technology mainstream.  Komodo's technology offering is vast.
* Multi-currency Wallet
* 3rd Generation Atomic Swap DEX Network
* Custom Consensus Framework
* Blockchain Starter Kit
* Blockchain Security Service