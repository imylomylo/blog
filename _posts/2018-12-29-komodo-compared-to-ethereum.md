---
id: 405
title: 'Komodo compared to Ethereum &#038; ETH architecture problems'
date: 2018-12-29T08:27:11+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=405
permalink: /komodo-compared-to-ethereum/
categories:
  - blockchain
  - komodo
image: wp-content/uploads/2018/12/4.-notarizing-onto-assetchains-768x721.png
---
Lately I have seen more questions asked on what is Komodo compared to Ethereum?  Ethereum architecture problems are well known currently and the dev team is working on it &#8211; or has been thinking/working on it for some time.  This [tweet storm about ethereum architecture](https://twitter.com/TuurDemeester/status/1078682801954799617) problems and more (economic changes etc.) is epic and brutally honest in my opinion.  Has some good references to back up the argument.

ETH&#8217;s whitepaper directly highlights the limitations of bitcoin.   These limitations are arguably in place so that the project does things a certain way &#8211; not provide a general purpose blockchain.  Whether the ethereum architecture problem needs to be highlighted has been covered by many projects and bloggers.

## Komodo Compared To Ethereum

I was fortunate enough to get curious on what komodo compared to ethereum was like for a [komodo tech tuesday](https://www.komodoplatform.com/tech-tuesday-update-13/) in early december 2018.  The architectural advantages of Komodo compared to Ethereum needed to be [highlighted for an infographic competition](https://www.komodoplatform.com/tech-tuesday-update-3/) to assist graphic designers in understanding how [komodo solves blockchain scalability](https://komodoplatform.com/komodo-platforms-new-scalability-tech/), here is an earlier post about [blockchain scaling tests on AWS](https://i.mylomylo.com/komodo-blockchain-scaling-1-million-tx-per-second-stats-prep-etc/) infrastructure prior to komodo being recognised as a [blockchain innovation leader](https://komodoplatform.com/komodo-platform-a-commitment-to-innovation/) and [becoming an AWS advanced tech partner](https://www.reddit.com/r/komodoplatform/comments/a19jkk/when_did_kmd_partner_with_aws/).

## Blockchain Scalability With Sharding

In the tweet storm linked in the intro, the author mentions a lot of sharding and proof of stake stuff.   The most efficient way to achieve peer2peer scalability is by sharding.  There&#8217;s many ways to do sharding, like any architecture.  I&#8217;m not an expert in sharding methods so cannot preach about the holy grail methods of doing it, but it works.  It&#8217;s been done with databases for years and now it&#8217;s working with blockchain technology.

How komodo does it is:

  * Multi-chain architecture
  * Fungibility between chains
  * Burn protocol to maintain coin supply

The secret to this lies in MoM technology &#8211; simply &#8211; merkle root of merkle roots.

<img class="aligncenter wp-image-407 size-full" src="https://i.mylomylo.com/wp-content/uploads/2018/12/merkle-root-of-merkle-roots-v2-768x368.png" alt="merkle root of merkle roots" width="768" height="368" srcset="https://i.mylomylo.com/wp-content/uploads/2018/12/merkle-root-of-merkle-roots-v2-768x368.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/12/merkle-root-of-merkle-roots-v2-768x368-300x144.png 300w" sizes="(max-width: 768px) 100vw, 768px" /> 

&nbsp;

Between chains an on-chain oracle needs to observe the MoMs and broadcast them to all participating chains in the cluster.

<img class="aligncenter wp-image-408 size-full" src="https://i.mylomylo.com/wp-content/uploads/2018/12/2.-sync-to-KMD-768x551.png" alt="sync to main chain" width="768" height="551" srcset="https://i.mylomylo.com/wp-content/uploads/2018/12/2.-sync-to-KMD-768x551.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/12/2.-sync-to-KMD-768x551-300x215.png 300w" sizes="(max-width: 768px) 100vw, 768px" /><img class="aligncenter wp-image-409 size-full" src="https://i.mylomylo.com/wp-content/uploads/2018/12/4.-notarizing-onto-assetchains-768x721.png" alt="sync from main chain" width="768" height="721" srcset="https://i.mylomylo.com/wp-content/uploads/2018/12/4.-notarizing-onto-assetchains-768x721.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/12/4.-notarizing-onto-assetchains-768x721-300x282.png 300w" sizes="(max-width: 768px) 100vw, 768px" /> 

## Ecosystem Innovation & Abrasive Responses

Ecosystem comparisons of Komodo compared to Ethereum would be unfair and biased at this point.  I think Komodo is great, and the ecosystem (through Verus lead dev &#8211; and ahem, architect of Microsoft .net platform) can [collaboratively solve blockchain problems](https://medium.com/veruscoin/how-verus-solved-nothing-at-stake-and-weak-subjectivity-proof-of-stake-problems-b4dd6a85086e) e.g. with proof of stake chains.  It is [interesting the statements that come out of the eth thought leaders](https://twitter.com/VladZamfir/status/1050842019835260928).  But they have been working on [&#8220;cooler&#8221; sharding technologies than MoM](https://twitter.com/VladZamfir/status/1071145665332310016) recently.  Time will tell whether the linked tweet storm holds more truth than rage-tweeting.

&nbsp;
