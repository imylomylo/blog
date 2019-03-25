---
id: 298
title: DynamoDB to CSV in a couple of commands
date: 2018-06-14T03:49:26+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=298
permalink: /dynamodb-to-csv-in-a-couple-of-commands/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
categories:
  - aws
  - serverless
---
DynamoDB to CSV is not as easy as it sounds &#8211; but can be crunched in a couple of commands.  During the [Komodo blockchain scaling](https://i.mylomylo.com/komodo-blockchain-scaling-1-million-tx-per-second-stats-prep-etc/) stuff we&#8217;re doing, in a simple scaled down run of about 1k tx/s we ended up with 40k items in a DynamoDB table.  To convert to csv, I did these commands using jq

<pre class="p1"><span class="s1">aws dynamodb scan --table-name kmd-blocknotify-blackjok3r-1-v0 &gt; result.json</span>

<span class="s1"> jq ".Items[] | [ .ac.S, .height.N, .totaltx.N, .size.N, .time.N, .mempoolMB.N, .mempooltx.N] | @csv" result.json<span class="Apple-converted-space">  </span>| sed 's/"//g' | sed 's/\\//g' &gt; result.csv</span>

</pre>

<p class="p1">
  Then to sort by a particular column
</p>

<pre class="p1"><span class="s1">cat result.csv | sort --field-separator=',' --key=5 &gt; sorted.csv</span></pre>

Easy to handle in a spreadsheet now 🙂