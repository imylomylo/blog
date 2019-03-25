---
id: 77
title: 'Agama FAQ &#8211; First Install, Updating &#038; User Data'
date: 2017-12-06T12:58:14+00:00
author: Mylo Mylo
layout: post
guid: https://i.mylomylo.com/?p=77
permalink: /agama-wallet-app-first-install/
royal-magazine-meta-select-layout:
  - left-sidebar
royal-magazine-meta-image-layout:
  - full
image: /wp-content/uploads/2017/12/choose-agama-mode.png
categories:
  - blockchain
tags:
  - komodo
---
Installing Agama FAQs? Didn&#8217;t look &#8211; too bleeding edge perhaps <del>I don&#8217;t think they exist yet</del> (edit:  I found the Agama [FAQ here](https://support.supernet.org/support/solutions/29000033391)!).  The first question is, where do you get it from?  There are 3 different version (numbers) available to download from public websites &#8211; not ideal, but the very friendly developers are within a few minutes of answering questions!

I may have come across a little short in the slack channel, but [opened an issue on github](https://github.com/SuperNETorg/Agama/issues/245), with a quick response that should be known:

The [wallet downloads page](https://komodoplatform.com/en/wallets#_desktop-wallets-multi) has 2 links.  One with the download button, this is the release and usually in sync with the [github release page](https://github.com/SuperNETorg/Agama/releases).  The &#8220;release&#8221; link is actually a [link to the jenkins build output](https://artifacts.supernet.org/latest/installer_osx.html), so it&#8217;s bleeding edge.

There was a recent bug, so the release engineering got out of sync.  It happens.

The next question is,

## How do you update Agama?

When you run the installer, select &#8220;re-install&#8221;.

## Do you have to download zcash keys and blockchain again?

No!  The installer never touches the underlying user data.  Komodo blockchain (currently 2.7GB) again?

## Choose Agama Mode & Add Coin Native Mode

Are these the same?  The dropdown menu of the screenshot at the top is a &#8220;shortcut to add coins&#8221; &#8211; so it&#8217;s essentially the same.  It&#8217;s probably there whilst the developers are doing their testing, so in the future maybe there&#8217;ll be a dev-mode flag in the settings or some kind of coin-profile for quick setup.

[<img class="aligncenter wp-image-82 size-medium" src="https://i.mylomylo.com/wp-content/uploads/2017/12/are-these-the-same-300x269.png" alt="Agama wallet mode and adding coin native mode" width="300" height="269" srcset="https://i.mylomylo.com/wp-content/uploads/2017/12/are-these-the-same-300x269.png 300w, https://i.mylomylo.com/wp-content/uploads/2017/12/are-these-the-same-768x689.png 768w, https://i.mylomylo.com/wp-content/uploads/2017/12/are-these-the-same.png 972w" sizes="(max-width: 300px) 100vw, 300px" />](https://i.mylomylo.com/wp-content/uploads/2017/12/are-these-the-same.png)

## Can you transfer the blockchain to save downloading?

Yes.  Just make sure the komodo daemon is not running then you can copy wallet.dat.  [Backing up on Wallet FAQs](https://support.supernet.org/support/solutions/articles/29000010041-how-to-take-backup-in-the-native-mode), the location of the blockchain varies depending on your platform (win/mac/lin).

The at-home internet here in Sydney is pretty crappy compared to other countries, so this question will have to be updated when I find out&#8230;the long download and wait to see what happens way.  It&#8217;s late and I&#8217;ve got stuff to do in the morning&#8230;like watch the alts burn (I was told to sic &#8220;stop dreaming&#8221; on the komodo slack channel about how alts seem to hold their btc value in satoshis&#8230;not that I really care &#8211; my holdings are play money for development).

## Initial Conclusion

With little documentation and a lot of options at download and install, (Edit: <del>the user experience sucks!)</del>  it took 10 minutes for the devs to answer some of my annoying questions, but they did and now that I know the answers, user experience judgement is on hold!  These guys are really really good at what they do.  Whatever I&#8217;m whinging about right now, they would have fixed before someone really cares to read this.  I know the tech is good from a systems, network protocols and innovation perspective.  The GUI is quite nice to look at as well &#8211; but the initial download and install &#8211; needs a bit of polishing to get more adoption.  I&#8217;m going to plug away at it because&#8230;.komodo tech is very innovative and very good.