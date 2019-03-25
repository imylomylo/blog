---
id: 327
title: Pre alpha komodo utxo smart contracts notes
date: 2018-08-22T05:35:34+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=327
permalink: /pre-alpha-komodo-utxo-smart-contracts/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2018/08/docker-kmd-jl777-dev.png
categories:
  - docker
  - komodo
tags:
  - smart contract
---
This is not even a blog post about Komodo&#8217;s UTXO Smart Contracts based on the [IETF&#8217;s Crypto Conditions standard](https://tools.ietf.org/html/draft-thomas-crypto-conditions-04) (which is currently in draft).  It&#8217;s just some notes on the path to working with Komodo Smart Contracts when they are released around Q1 2019.  If you are a dev, there&#8217;s nothing to do but have a read.  Upcoming posts will give details on writing blockchain apps using komodo&#8217;s new utxo smart contracts system.

## Why do it like this?

Front end devs really don&#8217;t want to [build server side software from source](https://i.mylomylo.com/build-komodo-source/), let alone learn about [getting a blockchain up and running](https://i.mylomylo.com/create-a-blockchain-project-from-zero-to-hero/), even though it is only two commands on different servers.  They just want to use the libraries and see the results.  This is the start of that journey.  The end goal is to get new devs into Komodo and the new UTXO Smart Contracts in less than 10 minutes.

## Why would a developer use Komodo?

Komodo lowers the barriers to blockchain and recycles bitcoin&#8217;s energy to secure independent chains.  There is also the ecosystem, app development, [security](https://i.mylomylo.com/blockchain-security-for-dapps-ecosystems/), scalability, interoperability.  A white label wallet, white label dex, and soon a white label crowd funding app with no middle man for peer to peer social venture capital.

## What does Pre-Alpha mean?

Lead dev of Komodo, [jl777, is working on his github repo/branch](https://github.com/jl777/komodo/tree/jl777/src/cc) which we are following.  Sometimes there are breaking changes whilst komodo utxo smart contracts are in heavy development.  To help with my own workflow, I&#8217;ve started straight away with docker so I can test the same stuff between a linux server and a mac laptop.

The [docker file is also on github](https://github.com/imylomylo/docker-komodo-smartcontracts) which when you build it for yourself, pulls the latest and compiles everything.  You end up with an image similar to the one on dockerhub depending on when you built it.

## Build your own docker komodo utxo smart contracts image

This is what I&#8217;ve done for a first attempt at publishing to docker hub with a reasonable naming convention.  Whilst I was learning the workflow, I made non-sustainable naming 🙂<figure id="attachment_331" style="width: 949px" class="wp-caption aligncenter">

<img class="wp-image-331 size-full" src="https://i.mylomylo.com/wp-content/uploads/2018/08/docker-komodo-utxo-smart-contracts-naming-quandry.png" alt="Some badly named docker images" width="949" height="225" srcset="https://i.mylomylo.com/wp-content/uploads/2018/08/docker-komodo-utxo-smart-contracts-naming-quandry.png 949w, https://i.mylomylo.com/wp-content/uploads/2018/08/docker-komodo-utxo-smart-contracts-naming-quandry-300x71.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/08/docker-komodo-utxo-smart-contracts-naming-quandry-768x182.png 768w" sizes="(max-width: 949px) 100vw, 949px" /> <figcaption class="wp-caption-text">Don&#8217;t put dates in image names. Also when building from different branches, too broader name doesn&#8217;t really describe enough at a glance.</figcaption></figure> 

Get started in 10 seconds, open a terminal, go to your dev directory and:

<pre>git clone https://github.com/imylomylo/docker-komodo-smartcontracts

cd docker-komodo-smartcontracts

sudo docker build -t imylomylo/kmd-jl777-dev:20180822a .</pre>

Depending on the speed of your internet/machine, I&#8217;m building on an atom server in france, shouldn&#8217;t take long (maybe 5 mins).  Time to keep hydrated or stimulated &#8211; courses for horses, you&#8217;ve got some time to get up stretch.

Otherwise, onto the javascript RPC lib I&#8217;ve been making to simplify dev.

&nbsp;

## Komodo RPC from localhost

As a contributor to the Komodo project, I&#8217;ve had a chance to give my opinion when the time has been appropriate &#8211; and that is to make it easier to develop with this blockchain project.  The work of jl777 on this utxo smart contracts system really needs to be easy to use.  There is no easier way to get started than directly with the daemon&#8217;s RPC (remote procedure call).

All blockchains offer this, so this is kind of portable.  You make an app for one blockchain, a lot of the RPC calls will be similar.  Building on top of a the stdrpc lib, and going through all of Komodo&#8217;s RPC methods (there&#8217;s more than most other chains) to flesh out a skeleton.<figure id="attachment_333" style="width: 640px" class="wp-caption aligncenter">

<img class="wp-image-333 size-large" src="https://i.mylomylo.com/wp-content/uploads/2018/08/kmd-rpc-lib-skeleton-1024x1022.png" alt="Skeleton RPC library" width="640" height="639" srcset="https://i.mylomylo.com/wp-content/uploads/2018/08/kmd-rpc-lib-skeleton-1024x1022.png 1024w, https://i.mylomylo.com/wp-content/uploads/2018/08/kmd-rpc-lib-skeleton-150x150.png 150w, https://i.mylomylo.com/wp-content/uploads/2018/08/kmd-rpc-lib-skeleton-300x300.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/08/kmd-rpc-lib-skeleton-768x767.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/08/kmd-rpc-lib-skeleton.png 1093w" sizes="(max-width: 640px) 100vw, 640px" /> <figcaption class="wp-caption-text">Skeleton RPC library. Note faucet, rewards, assets and dice. These are the first 4 smart contracts and their corresponding RPC commands for interacting with them.</figcaption></figure> 

The only calls that have been tested from both nodejs (the [komodo-rpc-lib project is by default a nodejs app](https://github.com/imylomylo/komodo-rpc-lib)) and a [vuejs app](https://github.com/imylomylo/komodo-cakeshop) at the moment are getinfo and stop.  The others that don&#8217;t take any arguments, like help, listunspent, getnewaddress etc. probably work too.

[edit, clarify some points in following paragraph]

I want to take a look at the smart contracts written in C++.  The easiest is the [faucet smart contract](https://github.com/jl777/komodo/blob/dev/src/cc/faucet.cpp).  It is well commented and although I can read it and understand it &#8211; it&#8217;s been 15+ years since I&#8217;ve done any C++ work.  So the next best thing to provide is access to the already available &#8220;reference&#8221; smart contracts.  They are &#8220;reference&#8221; because for any new use case of a smart contract, the Komodo Platform envisions a dev to pick the contract-of-closest-fit and modify to their needs.

## Pushing an image to docker for utxo smart contract testing

Being such a noob at docker, I still haven&#8217;t configured to use it without sudo on the linux server 🙂<figure id="attachment_336" style="width: 866px" class="wp-caption aligncenter">

<img class="wp-image-336 size-full" src="https://i.mylomylo.com/wp-content/uploads/2018/08/sudo-docker-push.png" alt="Push a smart contracts image to docker hub" width="866" height="618" srcset="https://i.mylomylo.com/wp-content/uploads/2018/08/sudo-docker-push.png 866w, https://i.mylomylo.com/wp-content/uploads/2018/08/sudo-docker-push-300x214.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/08/sudo-docker-push-768x548.png 768w" sizes="(max-width: 866px) 100vw, 866px" /> <figcaption class="wp-caption-text">Note that I also call history because I&#8217;m not familiar with docker commands like a hardened devops engineer.</figcaption></figure> 

But it&#8217;s there hosted on docker hub now!  So I can test on my laptop, and give a more detailed tutorial on getting up and running in < 10 mins being a blockchain app developer.  It takes too long just to document this part of it &#8211; but it needs to happen for &#8230; the journey!