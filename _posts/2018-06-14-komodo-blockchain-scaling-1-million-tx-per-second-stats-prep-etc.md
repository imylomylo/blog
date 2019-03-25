---
id: 291
title: 'Komodo Blockchain Scaling &#8211; 1 million tx per second &#8211; stats &#8211; prep etc.'
date: 2018-06-14T02:29:10+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=291
permalink: /komodo-blockchain-scaling-1-million-tx-per-second-stats-prep-etc/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2018/06/crypto-cartography.png
categories:
  - komodo
---
Komodo blockchain scaling is a load test requiring a lot of resources, preparation, co-ordination and then statistics.  Any load test does.  My days at [Omnium World](http://omniumworld.com/) were about seeing how many users could upload their portfolio work to our servers.  My days using [asterisk](https://asterisk.org) and doing the occasional load tests for carriers to see how many concurrent calls their networks could handle.

We are using AWS for infrastructure &#8211; EC2, DynamoDB, S3, ECS and maybe another service or two.

[<img class="aligncenter size-large wp-image-294" src="https://i.mylomylo.com/wp-content/uploads/2018/06/Komodo-Scalability-Solutions-Architecture-1024x613.png" alt="Komodo AWS Blockchain Scaling" width="640" height="383" srcset="https://i.mylomylo.com/wp-content/uploads/2018/06/Komodo-Scalability-Solutions-Architecture-1024x613.png 1024w, https://i.mylomylo.com/wp-content/uploads/2018/06/Komodo-Scalability-Solutions-Architecture-300x179.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/06/Komodo-Scalability-Solutions-Architecture-768x459.png 768w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2018/06/Komodo-Scalability-Solutions-Architecture.png)

Notary node operator [blackjok3r](https://github.com/blackjok3rtt/) from the [a-team](https://github.com/KomodoPlatform/NotaryNodes/tree/master/proposals/a-team) has built a docker image (with help from [NN operator patchkez of dragonriders](https://github.com/KomodoPlatform/NotaryNodes/tree/master/proposals/patchkez)) for us to scale.  Testing with 64 chains, we created a [start parameter](https://github.com/imylomylo/komodo-aws-blast-control) using the serverless framework for a simple URL to poll to trigger the transaction blasters.

As the blasting of transaction happens across the chains, we use the blocknotify event to send the latest block info.  It is captured using [AWS API Gateway ->Lambda -> DynamoDB](https://github.com/imylomylo/scaletest-blocknotify).  Another serverless framework thing to speed us along.

We&#8217;re now at a stage of tuning to maximise the transactions per second, but more importantly &#8211; have statistics available for the public to view in realtime (or close to realtime) on our efforts.  Something like this is being prepared.

[<img class="aligncenter size-large wp-image-295" src="https://i.mylomylo.com/wp-content/uploads/2018/06/crypto-cartography-1024x942.png" alt="Blockchain stats" width="640" height="589" srcset="https://i.mylomylo.com/wp-content/uploads/2018/06/crypto-cartography-1024x942.png 1024w, https://i.mylomylo.com/wp-content/uploads/2018/06/crypto-cartography-300x276.png 300w, https://i.mylomylo.com/wp-content/uploads/2018/06/crypto-cartography-768x706.png 768w, https://i.mylomylo.com/wp-content/uploads/2018/06/crypto-cartography.png 1080w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2018/06/crypto-cartography.png)

Massaging [sample data](https://s3-ap-southeast-2.amazonaws.com/kmd-scaling/sorted.csv) for smk782&#8217;s stats site, [cryptocartography.io](http://cryptocartography.io/) is the work for the next day.

Stay tuned for more updates 😀

Checkout [Komodo Pioneers](https://komodopioneers.com) while you&#8217;re here!

&nbsp;