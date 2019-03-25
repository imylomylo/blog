---
id: 72
title: Komodod getinfo returns -28 error
date: 2017-12-06T05:15:38+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=72
permalink: /komodod-getinfo-returns-28-error/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
categories:
  - blockchain
tags:
  - komodo
---
I&#8217;m new to komodo and have had the server off for 2 weeks whilst working on other projects. I started komodod and when running the komodod-cli getinfo command receive an error code -28.  Not knowing what it is, I asked on slack:

> root@kmd:~/.komodo# /root/komodo/src/komodo-cli getinfo  
> error code: -28  
> error message:  
> Loading block index&#8230;

Don&#8217;t worry that I&#8217;m running it as root.  I&#8217;m in testing mode.

From the komodo slack group, I was quickly responded to with this helpful tidbit

> Now Komodod Instance taking Time To load block index on already downloaded blocks, It will complete In some time, Check for debug.log, where you can find clear info on whats going on&#8230;.

The debug.log file had this info in it:

> <p class="p1">
>   <span class="s1">2017-11-23 03:45:52 torcontrol thread exit</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:53 net thread interrupt</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:53 msghand thread interrupt</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:53 opencon thread interrupt</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:53 addcon thread interrupt</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:53 scheduler thread interrupt</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:54 Shutdown: In progress&#8230;</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:54 StopRPC: waiting for async rpc workers to stop</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:54 StopNode()</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:55 KomodoMiner terminated</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:55 KomodoMiner terminated</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-11-23 03:45:56 Shutdown: done</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 </span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Zcash version v1.0.8-5aacfee (2017-11-06 13:56:28 +0200)</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 AppInit2: parameter interaction: -bind set -> setting -listen=1</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 </span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Komodo version v1.0.8-5aacfee (2017-11-06 13:56:28 +0200)</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using OpenSSL version OpenSSL 1.1.0d<span class="Apple-converted-space">  </span>26 Jan 2017</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using BerkeleyDB version Berkeley DB 6.2.23: (March 28, 2016)</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Default data directory /root/.komodo</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using data directory /root/.komodo</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using config file /root/.komodo/komodo.conf</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using at most 125 connections (1024 file descriptors available)</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using 2 threads for script verification</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 scheduler thread start</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Loading verifying key from /root/.zcash-params/sprout-verifying.key</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Loaded verifying key in 0.021802s seconds.</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 WARNING: option -rpcbind was ignored because -rpcallowip was not specified, refusing to allow everyone to connect</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 HTTP: creating work queue of depth 16</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 HTTP: starting 4 worker threads</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Using wallet wallet.dat</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 init message: Verifying wallet&#8230;</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 CDBEnv::Open: LogDir=/root/.komodo/database ErrorFile=/root/.komodo/db.log pathIn.(/root/.komodo)</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Bound to 127.0.0.1:7770</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Cache configuration:</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 * Using 12.5MiB for block index database</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 * Using 29.9MiB for chain state database</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 * Using 57.6MiB for in-memory UTXO set</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 init message: Loading block index&#8230;</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:08 Opening LevelDB in /root/.komodo/blocks/index</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:09 Opened LevelDB successfully</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:09 Opening LevelDB in /root/.komodo/chainstate</span>
> </p>
> 
> <p class="p1">
>   <span class="s1">2017-12-06 04:46:09 Opened LevelDB successfully</span>
> </p>

So it&#8217;s syncing apparently.  See how long it takes!!