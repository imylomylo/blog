---
id: 184
title: 'Notarising blockchains &#8211; Westpac bank blockchain software example'
date: 2017-12-28T23:01:56+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=184
permalink: /notarising-blockchains-westpac-bank-blockchain-software-example/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2017/12/notarising-blockchains.png
categories:
  - blockchain
  - komodo
---
Notarising blockchains is an [innovation from the komodo platform](https://komodoplatform.com/security-delayed-proof-of-work-dpow/).  In a few words, it mitigates hacking attempts on the blockchain&#8217;s history.

Basically what happens when notarising blockchains, the hash of a block is written to another blockchain.  This effectively creates two blockchains with the recorded hash of a block (the hash of transactions in that block of time).  To hack the blockchain, the hacker would need to hack two blockchains to change the history of the hash that exists.  Considering the bitcoin network has 500x the computing power of google &#8211; [a sisyphean task!](https://en.wikipedia.org/wiki/Sisyphus)

## Notarising Blockchains to strengthen an existing example from Westpac Bank &#8211; Airplane Software

<span class="embed-youtube" style="text-align:center; display: block;"></span>

Take this cue at 7m 20s which is linked in the video to save you time from [Westpac](https://www.westpac.com.au/), one of the largest banks in Australia.

In Westpac&#8217;s example, an airplane checks it&#8217;s software by consensus with other planes and the network.  What this scenario could possibly be is an aviation software provider, say [Avilution](https://www.avilution.com/) &#8211; a shameless plug for my friend Mark Spencer who I met through telecommunications software development via [the asterisk project](https://asterisk.org).

Avilution may not be known for having a large blockchain network to secure it&#8217;s software &#8211; nor would they want to run a network of blockchain nodes to secure their software &#8211; it would be like running a network or servers in the age of cloud and serverless.  They may however choose to delegate the security to the bitcoin network.  To do so, Avilution or any other software provider could [create an asset on the komodo platform](https://docs.komodoplatform.com/komodo/create-Komodo-Assetchain.html) and use the delayed Proof of Work to secure their asset against their own asset&#8217;s blockchain -> komodo&#8217;s blockchain -> and finally bitcoin&#8217;s blockchain.

Hopefully this is a nice intro into the notarising innovation that came out of the Komodo Platform.