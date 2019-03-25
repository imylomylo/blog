---
id: 89
title: 'Komodo Native Mode &#8211; Saving Time Moving Blockchain Data'
date: 2018-02-05T13:38:32+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=89
permalink: /komodo-native-mode-moving-blockchain-data/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2017/12/waiting-zcash-params-komodo-native-mode.png
categories:
  - blockchain
  - komodo
tags:
  - komodo
---
After my [first install off Agama](https://i.mylomylo.com/agama-wallet-app-first-install/), I fiddled around and decided to delete KMD in [SPV Mode](https://bitcoin.org/en/glossary/simplified-payment-verification), it wasn&#8217;t really what I wanted.  Komodo Native Mode is the full blockchain experience, total unmitigated and righteous sovereignty.  You can do sensible things like, backup the wallet.dat &#8211; especially after sending/receiving transactions!

[<img class="aligncenter wp-image-90 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/add-kmd-native-mode-1024x671.png" alt="Select Komodo Native Mode" width="640" height="419" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/add-kmd-native-mode-1024x671.png 1024w, https://i.mylomylo.com/wp-content/uploads/2017/12/add-kmd-native-mode-300x197.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/add-kmd-native-mode-768x503.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/add-kmd-native-mode.png 1392w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2017/12/add-kmd-native-mode.png)The komodod (komodo daemon) is going to run in the background.  Click &#8216;Activate Coin&#8217; and you should be up and running&#8230;

But first the zcash params need to be downloaded.  I spent 10 minutes reading various [zcash concepts](https://github.com/zcash/zcash/wiki/Concepts-in-Zcash) and key burning ceremonies on the internet.  In short they are 900MB.  If you&#8217;ve downloaded it once, then just copy the relevant folder onto a usb drive and move them to another computer.

Otherwise you get this nice screen where the red flag at the bottom says zcash params are missing.  So, you download 900MB of keys.

[<img class="aligncenter wp-image-91 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/zcash-params-are-missing-1024x671.png" alt="Zcash Params Missing" width="640" height="419" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/zcash-params-are-missing-1024x671.png 1024w, https://i.mylomylo.com/wp-content/uploads/2017/12/zcash-params-are-missing-300x197.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/zcash-params-are-missing-768x503.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/zcash-params-are-missing.png 1392w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2017/12/zcash-params-are-missing.png)

It downloads zcash-params and you just wait for it to do it&#8217;s thing.  There&#8217;s no putting it into the background, just have to wait.  So you&#8217;re better off moving it from another machine to save you a lot of time.  On the different platforms, the zcash params are stored:

&nbsp;

> Linux: ~/.zcash-params
> 
> Windows:
> 
> Mac:

&nbsp;

Then you&#8217;re up to blockchain sync.  Let it start so you know where to put your blockchain data on the new machine &#8211; only takes 10 seconds or so.

[<img class="aligncenter wp-image-97 size-large" src="https://i.mylomylo.com/wp-content/uploads/2017/12/komodo-native-mode-syncing-1024x719.png" alt="Komodo Native Mode Blockchain Sync" width="640" height="449" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/komodo-native-mode-syncing-1024x719.png 1024w, https://i.mylomylo.com/wp-content/uploads/2017/12/komodo-native-mode-syncing-300x211.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/komodo-native-mode-syncing-768x539.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/komodo-native-mode-syncing.png 1178w" sizes="(max-width: 640px) 100vw, 640px" />](https://i.mylomylo.com/wp-content/uploads/2017/12/komodo-native-mode-syncing.png)

After quitting agama, move the chainstate and blocks directories from a closed agama instance that is synced.  You&#8217;ll find the location around your wallet.dat file

> Linux: ~/.komodo/wallet.dat  
> MacOS: ~/Library/Applications Support/Komodo/wallet.dat  
> Windows: %AppData%/Komodo/wallet.dat

On your new machine, copy the folder chainstate and blocks directories to the above locations.  Then start agama.  It will rescan the blocks and activate best chain in an hour or so compared to a full off-the-net resync.